# Setup new docker Host
### Simple Ansible playbook which prepare any Ubuntu server for launching sites with Docker.

Ansible version >= 1.9 required

#### What it does?
- Install docker and docker-compose
- Create Swap
- Create new sudo user
- Setup SSH (change port and close access for root user)

##### Installation
- `clone` this repo locally
- `cd` to created directory and install Ansible requirements:

  `sudo ansible-galaxy install -r requirements.yml`
  
- Open `docker-host-setup-playbook.yml` file and change installation variables, they are pretty self explainable.

~~~~
  # Set Admin pass (change before server setup)
  admin_user_name: CHANGE_ME
  admin_user_pass: CHANGE_ME
  # Can leave as is.
  docker_compose_version:  1.8.0
  swapfile_location: /swapfile
  swapfile_size: 1024M
  # Security vars.
  security_ssh_config_path: /etc/ssh/sshd_config
  security_sshd_name: ssh
  security_ssh_port: 22
~~~~

###### Ubuntu 12.04 - 15.10
- Open `inventory` file and change `0.0.0.0` with your server's ip address.
- Launch installation process with command:

  `ansible-playbook launch-jenkins-server-playbook.yml -i inventory`

###### Ubuntu 16.04
- Open `inventory16.04` file and change `0.0.0.0` with your server's ip address.
- Launch installation process with command:

    `ansible-playbook launch-jenkins-server-playbook.yml -i inventory16.04`
