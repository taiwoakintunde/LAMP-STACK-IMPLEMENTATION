# ProjectOne
**My very first PBL Project**
1. I have documented my research on SDLC and saved the file in SDLC folder

# Install Apache using Ubuntu’s package manage
1. update a list of packages in package manager
	`sudo apt update`

Here are the steps I took before installing apache on ubuntu

1. Created an instance in EC2 in AWS
2. Edited the inbound rules of the  security group to allow all trafic and changed the source to anywhere IPV4 
3. Ran this command `ssh -i "tammyta.pem" ubuntu@ec2-3-83-97-237.compute-1.amazonaws.com`  to change the directory to ubuntu

# To install Apache using Ubuntu

1. update a list of packages in package manager
`sudo apt update`
2. run apache2 package installation
`sudo apt install apache2`
3. To verify that apache2 is running as a Service in our OS, use following command
`sudo systemctl status apache2`

# To allow any traffic to our web server
1. I edited the inbound rules
2. added another rule; HTTP with the cdr blocks 0.0.0.0/0
Then I ran this command on ubuntun shell curl `http://localhost:80`

# To access Apache HTTP server on the web browser
1. we need to open this on the web browser http://http://3.83.97.237/
2. To check the public IP Address 
I ran the below command on ubuntu shell
`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`
[Apache HTTP server](http://3.83.97.237/)