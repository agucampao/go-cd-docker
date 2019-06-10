GIT_TAG := $(shell git rev-parse --short HEAD)

all: build tag push

build:
	docker build -t curso_gocd_ep_6:$(GIT_TAG) .

tag:
	docker login --username rhclaudio --password-stdin < ~/my_password.txt
	docker tag curso_gocd_ep_6:$(GIT_TAG) rhclaudio/curso_gocd_ep_6:$(GIT_TAG)
	docker tag curso_gocd_ep_6:$(GIT_TAG) rhclaudio/curso_gocd_ep_6:latest

push:
	docker push rhclaudio/curso_gocd_ep_6:$(GIT_TAG)

test:
	docker run -d -p 8080:80 --rm --name curso_gocd_ep_6 curso_gocd_ep_6:$(GIT_TAG)
	sleep 2
	curl localhost:8080

test_clean:
	docker rm -f curso_gocd_ep_6
