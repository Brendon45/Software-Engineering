# Fabric functions:

Fabric provides several built-in functions that you can use within your Fabric tasks to execute commands, manage files, and interact with remote servers. Some of the commonly used Fabric functions include:

## run:

- Executes a shell command on a remote server.

python
Copy code
from fabric import task

@task
def my_task(c):
    c.run("ls -l")

## sudo:

- Executes a shell command with sudo privileges on a remote server.

python
Copy code
from fabric import task

@task
def my_task(c):
    c.sudo("apt-get update")

## local:

- Executes a shell command on the local machine.

python
Copy code
from fabric import task

@task
def my_task(c):
    c.local("ls -l")

## put:

- Transfers a file or directory from the local machine to a remote server.

python
Copy code
from fabric import task

@task
def my_task(c):
    c.put("local_file.txt", "/remote/directory/")

## get:

- Transfers a file or directory from a remote server to the local machine.

python
Copy code
from fabric import task

@task
def my_task(c):
    c.get("/remote/file.txt", "local_directory/")

## cd:

- Changes the working directory on the remote server for subsequent commands.

python
Copy code
from fabric import task

@task
def my_task(c):
    with c.cd("/path/to/directory/"):
        c.run("ls -l")

## lcd:

- Changes the working directory on the local machine for subsequent commands.

python
Copy code
from fabric import task

@task
def my_task(c):
    with c.lcd("/path/to/directory/"):
        c.local("ls -l")

- These are just a few examples of Fabric functions you can use to automate tasks and manage remote servers. Each function provides different capabilities for interacting with remote servers and executing commands.
