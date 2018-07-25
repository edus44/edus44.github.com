all:
	vue serve --open
build:
	cd .. && ls | grep -v src | xargs -r rm -r
	vue build
	mv dist/* ..
	rm -r dist