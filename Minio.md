![](https://lh7-us.googleusercontent.com/-UCR3sPgLCW9HONd-hnOWVAOCSNOZQg1X8KviInmthwXjs8kiZL3f_IhUhj7qCJCzQEhbVhthqpem1FAvPLo3ycHML8PFWXOfwD6lXVMBLktY4QNzYnDvpY9t2MZkz_WR0QyEqcmeodcOUeGhV7MqoU)

[**Install Docker on Ubuntu**](#install-docker-on-ubuntu-)

[**Docker Compose File**](#install-docker-compose)

[**Add following script to docker-compose.yml**](#add-following-script-to-docker-composeyml)

[**Start the Docker Containers**](#start-the-docker-containers)

[**MinIO Client**](#minio-client)

[**Set Minio Alias**](#set-minio-alias)

[**Get information about MinIO**](#execute-a-command-inside-a-docker-container)

[**Execute a Command Inside a Docker Container**](#create-a-minio-bucket)

[**View Docker Container Logs**](https://docs.google.com/document/d/1wP01j1iayvUnq8MibVrihPYG2K7pqDaaxw_bs5APFaY/edit#heading=h.e4vscxehwmt0)

[**Open  a web page**](https://docs.google.com/document/d/1wP01j1iayvUnq8MibVrihPYG2K7pqDaaxw_bs5APFaY/edit#heading=h.4293gkvra8rg)

[**Create a MinIO Bucket**](#copy-object-to-minio-bucket)

[**Copy object to minIO bucket**](#all-objects-are-shown-in-the-below-screenshot)

[**All Objects are shown in the below screenshot**](https://docs.google.com/document/d/1wP01j1iayvUnq8MibVrihPYG2K7pqDaaxw_bs5APFaY/edit#heading=h.ohu12mylcjbm)

**Task Requirement :-** 

To set up an object storage system in a cluster using MinIO.

**Environment Details :-**

Operating System (OS): Ubuntu 22.04.3 LTS

CPU: 4

Storage: 8 GB

**List of Tools and Technologies :-**

**MinIO** - Latest Version (RELEASE.2023-08-16T20-17-30Z)

**Docker** - Version 24.0.5

**Sidekick**

**Tools Definition:-**

**MinIO:**

MinIO is a high-performance, S3 compatible object store. It is built for large scale AI/ML, data lake and database workloads.

**Docker:**

Docker is a platform that allows OS level virtualization which delivers software packages called containers.

**Sidekick:** Sidekick is a high-performance sidecar load-balancer. By attaching a tiny load balancer as a sidecar to each of the client application processes.


# Install Docker on Ubuntu :<a id="install-docker-on-ubuntu-"></a>

**Step 1 :
Update & Upgrade Packages Lists :** 
```
sudo apt update && sudo apt upgrade -y
```
**sudo:** This stands for "Superuser Do" and it's used to execute commands with elevated privileges. It allows you to make changes to your system that regular users wouldn't have permission to do.

**apt:** This is the package manager for Debian-based systems. It's used for handling packages—installing, updating, and removing them.

**update:** This command updates the local package database with the latest information about available packages. This is a speciﬁc command for apt. When you run sudo apt update, it doesn't actually update the packages on your system; instead, it updates the local database of available packages. This database is necessary for the package manager to know what packages are available, where to download them, and what versions exist.

**&&:** This is a logical operator that means "and." In this context, it's used to run the next command only if the previous one succeeds.

**upgrade -y:** This is another action for apt. It's telling apt to upgrade all installed packages to their latest versions (upgrade), and the -y flag means "yes" to any prompts, so it automatically agrees to the upgrades without asking for confirmation.

**Step 2:**
```
sudo apt install docker.io -y
```
**apt:** This is a command used on Debian-based Linux systems (like Ubuntu) to manage software packages—installing, updating, and removing them.

**install:** You're telling the package manager (apt) that you want to install a piece of software.

**docker.io:** This is the name of the software package you want to install. Docker is a platform that lets developers automate the deployment of applications inside containers.

**-y:** This is an option that stands for "yes." By including this, you're telling the package manager to answer "yes" to any prompts or confirmations during the installation process. It's a way to automate the installation without needing you to confirm each step.

**Step 3 :**
```
sudo apt install docker
```
**apt:** This is a package management command on Debian and Ubuntu-based systems. It's used to install, upgrade, or remove software packages.

**install:** This is the action you want snap to perform. You are telling it to install a software package.

**docker:** This is the name of the package you want to install. Docker is a platform that enables developers to automate the deployment of applications inside lightweight, portable containers.

**Step 4 :** 
```
sudo systemctl status docker
```
**systemctl:** This is a command used to control the systemd system and service manager on Linux. It can be used to query and interact with the state of system services.

**status:** This is an option for systemctl that you're using to ask for the current status of a service.

**docker:** This is the name of the service you are checking. In this case, it's Docker, which is a platform for automating the deployment of applications inside containers.

**Step 5:**
```
docker --version
```
**docker:** This is the command-line interface (CLI) for interacting with Docker. It provides a set of commands that allow you to manage Docker containers, images, networks, and other Docker-related resources.

**--version:** This is an option or flag that you pass to the docker command. When used with docker, it instructs Docker to display information about its version.

Reference : <https://phoenixnap.com/kb/install-docker-on-ubuntu-20-04>


# Install Docker Compose<a id="install-docker-compose"></a>

**Step 1:** 
```
sudo curl -SL https\://github.com/docker/compose/releases/download/v2.23.0/docker-compose-linux-x86\_64 -o /usr/local/bin/docker-compose
```
**curl:** This is a command-line tool for making HTTP requests. In this context, it is used to download a file.

**-SL:** These are options for curl:

**-S:** Shows errors but does not show progress meter.

**-L:** Follows redirects. If the requested page has moved to a different location, curl will automatically follow the redirect.

**https\://github.com/docker/compose/releases/download/v2.23.0/docker-compose-linux-x86\_64:** This is the URL from which the Docker Compose binary is being downloaded. It specifies the version (v2.23.0) and the target architecture (Linux x86\_64).

**-o /usr/local/bin/docker-compose:** This part of the command specifies the output file path where the downloaded file will be saved. In this case, it's /usr/local/bin/docker-compose, indicating that the Docker Compose binary will be stored in the /usr/local/bin/ directory and named docker-compose.

**Step 2: 
Test and execute compose commands using docker-compose.**
```
sudo chmod +x /usr/local/bin/docker-compose
```
**sudo:** This is a command that allows a permitted user to execute a command as the superuser or another user, as specified by the security policy. In this case, it's used to run the subsequent command with elevated privileges.

**chmod +x /usr/local/bin/docker-compose:** This command is changing the permissions of the docker-compose executable file. Let's break it down:

**chmod:** Stands for "change mode" and is a command used to change the permissions of a file or directory.

**+x:**  Adds the execute permission to the specified file.

**/usr/local/bin/docker-compose:** Specifies the path to the docker-compose executable file. This is the location where the executable is expected to be installed.

**Step 3 :**
```
docker-compose --version
```
**docker-compose:** This is the main command-line tool for defining and running multi-container Docker applications. It uses a YAML file to configure the application's services, networks, and volumes.

**--version:** This is an option or flag that you pass to the docker-compose command. When used with docker-compose, it instructs the tool to display information about its version. Essentially, it's asking Docker Compose to print its version number.

**Edit the docker-compose.yml File**
```
vi docker-compose.yml
```
**vi:** This is a text editor in Unix-like operating systems. It's a command-line tool for creating and editing text files.

**docker-compose.yml:** This is the name of the file you want to edit. It's a YAML file, which is often used to configure Docker Compose, a tool for defining and running multi-container Docker applications.

Press i to enter insert mode, where you can edit the ﬁle.

Use the arrow keys to navigate to the desired location in the ﬁle.

Press Esc to exit insert mode and return to command mode.

To save your changes, press : to enter command mode, then type w to write (save) the ﬁle and q to

quit Vi. You can combine these commands as :wq to save and exit.


# Add following script to docker-compose.yml:<a id="add-following-script-to-docker-composeyml"></a>
```
version: '3'

services:

  lb:
  
    image: minio/sidekick:v0.5.1
    
    ports:
    
      - 8080:8080
      
    command:
    
      - --health-path=/minio/health/ready
      
      - http\://minio{1...4}:9000
      
  minio1:
  
    image: minio/minio:RELEASE.2023-08-16T20-17-30Z
    
    environment:
    
      MINIO\_ACCESS\_KEY: admin
      
      MINIO\_SECRET\_KEY: redhat1234
      
    command: server http\://minio{1...4}/data
    
  minio2:
  
    image: minio/minio:RELEASE.2023-08-16T20-17-30Z
    
    environment:
    
      MINIO\_ACCESS\_KEY: admin
      
      MINIO\_SECRET\_KEY: redhat1234
      
    command: server http\://minio{1...4}/data
    
  minio3:
  
    image: minio/minio:RELEASE.2023-08-16T20-17-30Z
    
    environment:
    
      MINIO\_ACCESS\_KEY: admin
      
      MINIO\_SECRET\_KEY: redhat1234
      
    command: server http\://minio{1...4}/data
    
  minio4:
  
    image: minio/minio:RELEASE.2023-08-16T20-17-30Z
    
    environment:
    
      MINIO\_ACCESS\_KEY: admin
      
      MINIO\_SECRET\_KEY: redhat1234
      
    command: server http\://minio{1...4}/data
```    

#  Start the Docker Containers <a id="start-the-docker-containers"></a>

```
sudo docker-compose up -d
```
**docker-compose:** This is a tool for defining and running multi-container Docker applications. It allows you to manage and configure multiple Docker containers using a YAML file.

**up:** This is a command used with docker-compose to start and run the containers defined in the docker-compose.yml file.

**-d:** This flag stands for "detached." When you run Docker containers in detached mode, it means they run in the background and don't block the terminal.


# MinIO Client<a id="minio-client"></a>

Minio is a tool that helps you interact with Minio servers. 

Minio servers are like storage spaces where you can store and retrieve your files. 

The Minio client is the tool you use on your computer to talk to these storage spaces. 

It's a bit like having a remote control for your file storage—you can upload, download, and manage your files on a Minio server using the Minio client.

**Install MinIO Client**


**Step 1 :**
```
sudo curl https\://dl.min.io/client/mc/release/linux-amd64/mc --create-dirs -o $HOME/minio-binaries/mc
```
**curl**: A command-line tool for making HTTP requests and downloading files.

**https\://dl.min.io/client/mc/release/linux-amd64/mc:** The URL from which the MinIO client binary for Linux (64-bit) will be downloaded.

**--create-dirs:** A flag for curl indicating that it should create the necessary directories in the specified path if they don't exist. In this case, it's creating the minio-binaries directory in the user's home directory.

-**o $HOME/minio-binaries/mc**: Specifies the output file path for the downloaded binary. In this case, it's saving the MinIO client binary as mc in the minio-binaries directory inside the user's home directory ($HOME).

**Step 2 :**
```
chmod +x $HOME/minio-binaries/mc
```
**chmod:** Stands for "change mode," a command used in Unix-like operating systems to change the permissions of a file or directory.

**+x:** Adds the execute permission to the file. The +x means "add execute permissio`n."`

**$HOME/minio-binaries/mc:** Specifies the path to the MinIO client binary (mc) that you want to make executable. This path includes the user's home directory ($HOME), the directory where the MinIO client was saved (minio-binaries), and the filename (mc).

**Step 3 :**
```
export PATH=$PATH:$HOME/minio-binaries/
```
**export PATH=:** This command is used to set or modify the value of the PATH environment variable.

**$PATH::** The existing value of the PATH variable is preserved by using $PATH, and a colon (:) is added to separate it from the new directory.

**$HOME/minio-binaries/:** This is the directory path that you want to add to the PATH. It's the location where the MinIO client binary (mc) is stored.

**Step 4 :**
```
mc --help
```
**mc:** This is the MinIO client, a command-line tool used for interacting with MinIO servers. MinIO is an object storage server that is compatible with the S3 API.

**--help:** This is an option or flag that you can add to a command to get help or usage information. When you run mc --help, it displays a summary of available commands, options, and how to use them.

# Set Minio Alias<a id="set-minio-alias"></a>
```
mc alias set niteshminio <http://127.0.0.1:8080> admin redhat1234
```
**mc:** This is the MinIO client, a command-line tool used for interacting with MinIO servers.

**alias set:** This part of the command is telling mc that you want to set up an alias, which is a shorter, more convenient name for a specific MinIO server.

**niteshminio:** This is the alias name you are creating. You can choose any name you prefer. In this case, it's "niteshminio."

**http\://127.0.0.1:8080:** This is the URL of the MinIO server you want to connect to. In this example, it's a local server accessible at http\://127.0.0.1 on port 8080. Replace this with the actual address of your MinIO server.

**admin:** This is the access key or username to authenticate with the MinIO server.

**redhat1234:** This is the secret key or password to authenticate with the MinIO server.


# Get information about MinIO <a id="get-information-about-minio"></a>
```
mc admin info niteshminio
```
**mc:** This is the MinIO client, a command-line tool used for interacting with MinIO servers.

**admin info:** This part of the command instructs mc to retrieve information about the MinIO server, specifically administrative information.

**niteshminio:** This is the alias name representing the MinIO server for which you want to get information. Replace it with the alias you've set up for your specific MinIO server.


# Execute a Command Inside a Docker Container<a id="execute-a-command-inside-a-docker-container"></a>
```
sudo docker exec -it root\_lb\_1 "/sidekick" -a :8989 --health-path=/minio/health/ready [**http://minio{1...4}:9000**](about:blank)
```
**sudo docker exec:** Execute a command inside a running Docker container.

**-it:** Interactive mode, allowing you to interact with the command being executed.

**root\_lb\_1:** The name or ID of the Docker container to run the command in.

**"/sidekick":** The command or script to run inside the container. In this case, it's "sidekick."

**-a :8989:** Additional options for the command inside the container. -a specifies an option, and :8989 indicates that the program should use port 8989.

**--health-path=/minio/health/ready:** Another option for the command, likely specifying a health check path. The health check ensures that the program or container is functioning correctly. In this case, it's checking the health at the path "/minio/health/ready."

**http\://minio{1...4}:9000:** This is likely an argument or parameter passed to the "sidekick" script. It could be specifying a range of MinIO server addresses from minio1:9000 to minio4:9000.

Maybe it is your personal choice but according to me the alignment of the content is not so good.

**View Docker Container Logs**
```
sudo docker logs -f nitesh\_minio\_1
```
**sudo docker logs:** This part of the command is telling Docker to display the logs of a specific container.

**-f:** The -f flag stands for "follow," which means it will continuously show the latest log entries as they are generated.

**nitesh\_minio\_1:** This is the name or ID of the Docker container for which you want to see the logs. Replace it with the actual name or ID of your container.

**Open  a web page**

**Link :** http\://172.18.0.2:45697


# Create a MinIO Bucket<a id="create-a-minio-bucket"></a>
```
mc mb niteshminio/niteshbucket
```
**mc:** This is the MinIO client, a command-line tool used for interacting with MinIO servers.

**mb:** Stands for "make bucket." This command is used to create a new bucket on a MinIO server.

**niteshminio/niteshbucket:** This is the full path to the new bucket. "niteshminio" is the alias representing the MinIO server, and "niteshbucket" is the name of the new bucket you're creating.


# Copy object to minIO bucket.<a id="copy-object-to-minio-bucket"></a>
```
mc cp /home/nitesh/Downloads/postgresql-16-A4.pdf niteshminio/niteshbucket
```
**mc:** This is the MinIO client, a command-line tool used for interacting with MinIO servers.

**cp:** Stands for "copy." This command is used to copy files or objects between locations.

**/home/nitesh/Downloads/postgresql-16-A4.pdf:** This is the source file path on the local file system. It's the file you want to copy.

**niteshminio/niteshbucket:** This is the destination path within the MinIO server. "niteshminio" is the alias representing the MinIO server, and "niteshbucket" is the name of the target bucket. The copied file will be placed in this bucket.


# All Objects are shown in the below screenshot<a id="all-objects-are-shown-in-the-below-screenshot"></a>
```
mc ls niteshminio/niteshbucket
```
**mc:** This is the MinIO client, a command-line tool used for interacting with MinIO servers.

**ls:** Stands for "list." This command is used to display a list of objects/files within a specified bucket or directory.

**niteshminio/niteshbucket:** This is the path to the bucket within the MinIO server. "niteshminio" is the alias representing the MinIO server, and "niteshbucket" is the name of the bucket.
