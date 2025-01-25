all: ubuntu2104.test ubuntu2110.test debian.test archlinux.test fedora.test

GITBRANCH=$(shell git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\1/')

gitbranch:
	echo $(GITBRANCH)

%.test:
	docker build -t $* ./$*/ && docker run --name=$* $* $(GITBRANCH) && docker cp $*:build/ov-client/packaging/deb/debian ./artifacts/ && docker container rm $* && touch $@

%.arm64:
	docker build --platform=linux/arm64/v8 -t $*_arm64 ./$*/ && docker run --platform=linux/arm64/v8 --name=$*_arm64 $*_arm64 $(GITBRANCH) && docker cp $*_arm64:build/ov-client/packaging/deb/debian ./artifacts/ && docker container rm $*_arm64 && touch $@

clean:
	rm -f *.test

dockerprune:
	docker system prune -a
