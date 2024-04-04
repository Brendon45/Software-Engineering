# Welcome to the 0x03. AirBnB clone - Deploy static & lets dive into some concepts:

## DevOps

## Python

## SysAdmin

## Scripting

## CI/CD

## Most asked questions:

	- What is Fabric
	- How to deploy code to a server easily
	- What is a tgz archive
	- How to execute Fabric command locally
	- How to execute Fabric command remotely
	- How to transfer files with Fabric
	- How to manage Nginx configuration
	- What is the difference between root and alias in a Nginx configuration

## 1. What is Fabric?

	- Fabric is a Python library and command-line tool that simplifies the process of automating tasks, particularly those related to deploying, managing, and configuring software on remote servers. 
	- It allows you to write Python scripts (known as Fabric tasks) to execute commands, transfer files, and perform various operations on multiple servers simultaneously.

## 2. How to deploy code to a server easily?

	- Fabric can help streamline the deployment process by automating repetitive tasks. 
	- You can write Fabric tasks to pull code from a version control system (e.g., Git), transfer files to the server, run deployment scripts, restart services, and more. 
	- By defining these tasks in Python scripts, you can execute them easily and consistently across multiple servers.

## 3. What is a tgz archive?

	- A tgz archive, also known as a tarball, is a compressed archive file format commonly used in Unix-like operating systems.
	- It combines multiple files and directories into a single file, preserving their directory structure.
	- The .tgz extension indicates that the archive has been created using the tar utility and compressed with gzip. Tarball archives are often used for packaging and distributing software or data.

## 4. How to execute Fabric command locally?

	- To execute Fabric commands locally, you can use the local function provided by Fabric. Inside a Fabric task, you can call local with the desired shell command as an argument. Fabric will then execute the command on the local machine. For example:

python
from fabric import task

@task
def my_local_task(c):
    c.local("ls -l")

## 5. How to execute Fabric command remotely?

	- To execute Fabric commands remotely on a server, you can use the run function provided by Fabric. Inside a Fabric task, you can call run with the desired shell command as an argument, specifying the remote host to execute the command on. For example:

python
from fabric import task

@task
def my_remote_task(c):
    c.run("ls -l", host="username@remote_host")

## 6. How to transfer files with Fabric?

	- Fabric provides the put and get functions to transfer files between the local machine and remote servers.
	- You can use put to upload files from the local machine to a remote server and get to download files from a remote server to the local machine. For example:

python
from fabric import task

@task
def transfer_file(c):
    c.put("local_file.txt", "/remote/directory/")
    c.get("/remote/file.txt", "local_directory/")

## 7. How to manage Nginx configuration?

	- To manage Nginx configuration, you can edit the configuration files directly using a text editor such as vim or nano.
	- Additionally, you can use tools like Fabric to automate tasks related to Nginx configuration, such as deploying configuration files, reloading Nginx service, or restarting Nginx after configuration changes.

## 8. Difference between root and alias in an Nginx configuration?

	- In Nginx configuration, root specifies the root directory for serving static files, while alias specifies an alternative location for serving static files. The key difference is how they handle URL path mapping:

		- root: Maps the URL directly to the file system path specified by root. For example, http://example.com/static/image.jpg would correspond to /var/www/html/static/image.jpg.

		- alias: Replaces part of the URL path with the specified directory path. For example, http://example.com/static/image.jpg would correspond to /var/www/html/images/image.jpg if alias /var/www/html/images/ is configured.

## Examples:


