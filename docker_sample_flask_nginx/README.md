# docker_sample_flask_nginx
a simple docker compose using flask nginx and redis

# Requirements:
docker-compose version 1.14.0

I use docker for mac, Docker Community Edition (ce)
Version 17.06.0-ce-mac19 (18663)

Note: I had to login with my docker account to build the nginx container.  Which requires a docker account.

	# url: https://www.docker.com/
	docker login

# How to use:
	
	# clone the repo into a directory
	mkdir my_dir
	cd my_dir
	git clone https://github.com/primusdj/docker_sample_flask_nginx.git .

	# in the directory with the docker-compose.yaml file run
	docker-compose build

	# if all went well with the build, note above.  Run the up command for docker-compose
	docker-compose up

	# test the site with a web browser.
	http://localhost:8080

	# when your done, clean up after yourself
	docker-compose down --volumes
