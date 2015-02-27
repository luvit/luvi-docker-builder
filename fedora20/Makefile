IMAGE_UUID := $(shell uuidgen)
CONTAINER_UUID := $(shell uuidgen)

default: docker

docker:
	cat Dockerfile | docker build --no-cache -t "$(IMAGE_UUID)" -
	docker run --name="$(CONTAINER_UUID)" "$(IMAGE_UUID)" /bin/bash
	docker cp $(CONTAINER_UUID):/build/package .
	docker rm "$(CONTAINER_UUID)"
	docker rmi "$(IMAGE_UUID)"

clean:
	rm -rf ./package
