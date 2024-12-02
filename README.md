# Overview
Here is a template for your web application written in PHP with Nginx as the web server.
You can define the entire stack configuration in a docker-compose file, along with configuration files for PHP, Nginx and your other services.

# Instruction
First make sure you have installed docker and docker-compose on your machine!
Then you should copy the file `.env.example` into `.env` and edit the variables. Now run the following command:

step 1:
	change your directory to the root of project for this project is /src

step 2:
	build the app
	RUN : sudo docker-compose build
	
step 3:
	docker-compose up -d

step 4:
	enjoy it!




#debugging
For debugging matter you can user below command to see the log:
	sudo docker-compose logs <name of the container>
	
#
