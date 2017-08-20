# Linux-Server-Configuration UDACITY FSND Project

## About This Project 
You will take a baseline installation of a Linux server and prepare it to host your web applications. You will secure your server from a number of attack vectors, install and configure a database server, and deploy one of your existing web applications onto it.
You will learn how to access, secure, and perform the initial configuration of a bare-bones Linux server. You will then learn how to install and configure a web and database server and actually host a web application.

## My Server Details 
<ul>
<li> Public IP Address : 13.126.236.233 </li>
<li> SSH Port : 2200 </li>
<li> Vist http://13.126.236.233/ for deployed site </li>
</ul>

## How to complete this Project ?

To complete this project, you'll need a Linux server instance. It is recommended using Amazon Lightsail for this. If you don't already have an Amazon Web Services account, you'll need to set one up. Once you've done that, here are the steps to complete this project :


### Get your Server

Start a new Ubuntu Linux server instance on Amazon Lightsail.To get started with lightsail follow the following instructions :
<ul>
<li> First, log in to Lightsail. If you don't already have an Amazon Web Services account, you'll be prompted to create one</li>
<li> Once you're logged in create an instance. </li>
<li> Choose an instance image.For this project, you'll want a plain Ubuntu Linux image.</li>
<li> Choose your instance plan.</li>
<li> Give your instance a hostname. </li>
<li> Wait for it to start up.It may take a few minutes for your instance to start up.</li>
<li> Once your instance has started up, you can log into it with SSH from your browser </li>
</ul>


### Secure Your Server

<ul>
<li>Update all currently installed packages using 
<code>sudo apt-get update</code> command</li>

<li>Change SSH port from 22 to 2200. First Run <code>sudo nano /etc/ssh/sshd_config</code>.Then change its port from 22 to 2200.Once you're done restart sshd : <code>sudo service sshd restart</code> . exit and try to ssh again without specifying a port, if all went well you should get an error. Then try again with specifying a port <code>-p 2200</code></li>

<li> Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)
<ul>
<li><code>sudo ufw allow 2200/tcp</code></li>
<li><code>sudo ufw allow 80/tcp</code></li>
<li><code>sudo ufw allow 123/tcp</code></li>
<li><code>sudo ufw enable</code></li>
</ul>
</li>
</ul>


### Give Grader Access

<ul>
<li> Create a new user account named grader using the command <code>sudo adduser grader</code></li>
<li>  Give grader the permission to sudo using <code>sudo usermod -aG sudo grader</code></li>
<li> Setup An ssh key for user grader. Follow the instructions given :
<ul>
<li> Switch to user grader using the command <code> su grader </code></li>
<li> Now create a .ssh directory using <code>mkdir ~/.ssh</code> </li>
<li> Run <code> sudo cp /home/ubuntu/.ssh/authorized_keys ~/.ssh/ </code> </li>
<li> setup the permissions and ownership rights using <code>sudo chown grader:grader /home/grader/.ssh/authorized_keys</code></li>
<li> At last Run <code> sudo chmod 700 /home/grader/.ssh </code> . This is just for good security practice. </li>
</ul></ul>


### Prepare to deploy your project
<ul>
<li> Run <code> sudo timedatectl set-timezone UTC </code> to Configure the local timezone to UTC.</li>
<li>Install Apache:

<code>sudo apt-get install apache2</code>

Install the libapache2-mod-wsgi package:

<code> sudo apt-get install libapache2-mod-wsgi </code>
</li>
<li> Install and configure PostgreSQL using command <code> sudo apt-get install postgresql </code></li>
<li> Install other python dependancies like psycopg2,sqlalchemy,oauth2client etc using the <code>sudo apt-get install</code> command</li>
<li> Create a new database user named catalog that has limited permissions to your catalog application database. </li>
<li> Install git using <code> sudo apt-get install git </code>
</ul>

### Deploy the Item Catalog project.
<ul>
<li> Clone and setup your Item Catalog project from the Github repository you created earlier in this Nanodegree program </li>
<li> Set it up in your server so that it functions correctly when visiting your server’s IP address in a browser. Make sure that your .git directory is not publicly accessible via a browser! </li>

</ul>
