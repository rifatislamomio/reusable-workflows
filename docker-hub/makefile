# Place this file inside source folder
VERSION:=v0.01
IMAGE_NAME:=backend
HOST_PORT:=8000
CONTAINER_PORT:=3000
CONTAINER_NAME:=backend
DOCKER_REGISTRY:=docker.io
DOCKER_USER:=${DOCKER_USERNAME}
DOCKER_PASSWORD:=${DOCKER_ACCESS_TOKEN}

build:
	@ docker build -t ${IMAGE_NAME}:${VERSION} .

run:
	@ docker run -p ${HOST_PORT}:${CONTAINER_PORT} -e APP_PORT=${CONTAINER_PORT} -name ${CONTAINER_NAME} ${IMAGE_NAME}:${VERSION}

rm:
	@ docker stop ${CONTAINER_NAME}
	@ docker rm ${CONTAINER_NAME}

docker-login:
	@ echo "Docker Login"
	@ echo ${DOCKER_PASSWORD} | docker login -u ${DOCKER_USER} --password-stdin ${DOCKER_REGISTRY}

docker-push:
	@ docker tag ${IMAGE_NAME}:${VERSION} ${DOCKER_USER}/${IMAGE_NAME}:${VERSION}
	@ docker push ${DOCKER_USER}/${IMAGE_NAME}:${VERSION}