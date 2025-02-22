# DevOps

STEPS
Create a Dockerfile
Add instructions in Dockerfile to create Docker image
Run Dockerfile to create Docker image
Run Docker image to create Docker container
Access the application running in Docker container

Dockerfile ＞ Docker Image ＞ Docker Container ＞ Access the App

Step 1 - Create a new directory mkdir myapp
       cd myapp   

Step 2 - Create a file called "index.html" echo "Hello, world!" ＞ index.html

Step 3 - Create a file named Dockerfile  touch Dockerfile

Step 4 - Open the "Dockerfile" file in a text editor and add the following lines:

FROM nginx
COPY index.html /usr/share/nginx/html

This Dockerfile defines a new Docker image that 
uses the official nginx image as a base
then copy the index.html file to the appropriate location in the image

A Dockerfile is a text file with instructions to build a Docker Image
When we run a Dockerfile, Docker image is created
When we run the docker image, containers are created

Step 5 - Start docker & Build docker image from dockerfile 
docker build -t myapp .
This command builds a new Docker image with the tag "myapp" using the Dockerfile in the current directory.

Step 6 - Run docker container from the image   
docker run -p 8080:80 myapp
This tells Docker to run the myapp container and map port 8080 on your local machine to port 80 inside the container

Step 7 - Access the app
Open a web browser and navigate to http://localhost:8080 to see the "Hello, world!" message displayed in your web browser.

If you are using AWS EC2 Linux, you will need to make sure that the security group for your AWS Linux instance allows inbound traffic on port 8080 (or whichever port you chose to map to port 80 inside the container).

Here's how to modify the security group:

Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.
In the navigation pane, choose "Instances".
Select your AWS Linux instance in the list.
Choose the "Security" tab in the bottom pane.
Select the security group associated with your instance and choose the "Edit inbound rules" button.
Add a new rule with the following settings:
Type: "Custom TCP Rule"
Protocol: "TCP"
Port Range: "8080" (or whichever port you chose to map to port 80 inside the container)
Source: "0.0.0.0/0" (or restrict the source IP address range to your specific needs)
After modifying the security group, you should be able to access the web page served by your Docker container by navigating to http://＜Public_IP_of_your_instance＞:8080 in a web browser.
