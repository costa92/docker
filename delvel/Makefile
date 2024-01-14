PROJECT_NAME :=go-base-debug
BUILD_NAME :=$(subst -,_,$(PROJECT_NAME))

TKE_HOST := costa92
LOCAL_TAG := v1.0.0

DOCKER_IMAGE_TKE_LOCAL := $(TKE_HOST)/$(PROJECT_NAME):$(LOCAL_TAG)
.SECONDARY: $(wildcard Dockerfile)
Dockerfile:
	docker build -t $(PROJECT_NAME) .

build-linux:
	docker buildx build -t $(DOCKER_IMAGE_TKE_LOCAL) --platform linux/amd64 . --push
	

build-mac:
	docker build -q  -t $(DOCKER_IMAGE_TKE_LOCAL) . 

buildx_info:
	docker buildx inspect --bootstrap


build_create:
	docker buildx create --name pensive_keller &&\
	docker buildx use pensive_keller 

bulidx:
	docker buildx build --load -t $(DOCKER_IMAGE_TKE_LOCAL) --platform linux/arm64 .

push:
	docker push $(DOCKER_IMAGE_TKE_LOCAL)
version:
	@docker run $(DOCKER_IMAGE_TKE_LOCAL) dlv version

cache:
	@docker system prune -a --force	