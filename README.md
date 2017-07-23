# FSND-Linux-Server-Configuration

IP Address: 52.41.99.24

SSH Port: 2222

URL: http://ec2-52-41-99-24.us-west-2.compute.amazonaws.com

### Summary of configuration changes made
##### Followed the Project Details provided in the Udacity Linux Configuration - Project Details page

#### Get your server.

1. Start a new Ubuntu Linux server instance on Amazon Lightsail. There are full details on setting up your Lightsail instance on the next page.
2. Follow the instructions provided to SSH into your server.

#### Secure your server.

3. Update all currently installed packages.

    `sudo apt-get update`
    
    `sudo apt-get upgrade`
    
4. Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.

    `sudo nano /etc/ssh/sshd_config` update port from 22 to port of your choice
    
5. Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2222), HTTP (port 80), and NTP (port 123).

    `sudo ufw status numbered` to list all rules currently applied
    
    `sudo ufw allow 80`
    
    `sudo ufw allow 123`
    
    `sudo ufw allow 2222`
    
    `sudo ufw status numbered` to list the active rules
    
    `sudo ufw delete #` to delete any rule other than ports 80, 123, 2222
    
    `sudo ufw reload` to apply the rules and restart the firewall
    
6. Create a new user account named grader.

    `adduser username` to create a user, you will be prompted for a password.
    
7. Give grader the permission to sudo.

        `usermod -aG sudo username` to add the user to the sudo group.
        
8. Create an SSH key pair for grader using the ssh-keygen tool.

    Use the following DigitalOcean guide on generating the SSH key pair
    
        https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

#### Prepare to deploy your project.

9. Configure the local timezone to UTC.

    `sudo dpkg-reconfigure tzdata` select **'None of the above'** then **'UTC'**
    
10. Install and configure Apache to serve a Python mod_wsgi application.

    Use the following DigitalOcean guide on installing and configuring Apache and mod_wsgi
    
        https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

11. Install and configure PostgreSQL

    Use the following DigitalOcean guide on installing and configuring PostgreSQL and a PostgreSQL role
    
        https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04

