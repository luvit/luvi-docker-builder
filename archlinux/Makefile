IMAGE_UUID := $(shell uuidgen | tr "[:upper:]" "[:lower:]")

default: docker

docker:
	docker build --no-cache -t "$(IMAGE_UUID)" .
	docker run --rm -u `id -u`:`id -g` -v `pwd`:/OUT "$(IMAGE_UUID)" /bin/bash -c "cp -r /build/package/ /OUT/"
	docker rmi "$(IMAGE_UUID)"

clean:
	rm -rf ./package
