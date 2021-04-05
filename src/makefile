build:
	cd .. && ls | grep -v src | xargs -r rm -r
	cd src
	yarn build
	mv dist/* ..
	rm -r dist