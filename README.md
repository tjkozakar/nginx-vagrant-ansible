# nginx-vagrant-ansible
Deploy and launch nginx:alpine docker container with Vagrant &amp; Ansible


This project seeks to build a local development environment for nginx webserver testing by utilizing Vagrant, Ansible and Docker. The assumption is made that you have a MacOS operating system operating locally. For easier package management, you should preemptively install Homebrew. Visit brew.sh for further instructions.

Furthermore, you will need Oracle VirtualBox to launch the Vagrant images properly on your local environment. Visit https://www.virtualbox.org/wiki/Downloads to download and configure the application files. 

Brew commands:

1. brew tap hashicorp/tap
2. brew install vagrant
3. brew install ansible

Once these commands have completed, and you have successfully downloaded and installed VirtualBox onto your local machine, all necessary components for launching this program should be complete. 


The aim of this application is simple: run a single command that automatically configures an nginx:alpine web container provided by Docker. While this could normally be achieved by simply running the docker container manually on your command line, I wanted to emulate a CentOS7 server environment running a docker container via an open port. The base Vagrantfile performs the necessary steps of configuring a lightweight server with basic networking attachments for SSH and HTTP access. However, the Vagrantfile does not contain the necessary configurations for installing and configuring the core Docker software, along with its dependencies. To achieve this, I set up a simple Ansible provisioner step in the Vagrantfile which utilizes the attached dockerize-playbook.yml file. 

systemd is utilized in this infrastructure stack to daemonize the nginx:alpine docker container. Attached to this repo you should see a docker.nginx.service unit file, and there should be no user interraction needed for further configuration. Ansible copies this file into the proper destination, enables and starts the service at runtime. 

The end user should only need to run a single command for the entire infrastructure to deploy and server web requests: 

1. vagrant up --provision. 


Proceed to your web browser and check localhost:8086 to view the welcoming nginx screen. 
