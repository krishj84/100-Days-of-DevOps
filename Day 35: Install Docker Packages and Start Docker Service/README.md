The Nautilus DevOps team aims to containerize various applications following a recent meeting with the application development team. They intend to conduct testing with the following steps:

Install docker-ce and docker compose packages on App Server 2.

Initiate the docker service.

Solution:

1.  Install dnf-plugins-core and set up the repository:

    sudo dnf -y install dnf-plugins-core
   
    sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo # For CentOS/RHEL

2.  Install Docker CE and the Compose plugin:
   
    sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

3.  Start and enable the Docker service:

    sudo systemctl enable --now docker

4. To add an existing user to a group

   usermod -aG docker steve

   - G --> means set supplementary groups
   - a --> Stands for append , It ensures the user is added to the group without removing existing group memberships

5. Verify the installation

   docker run hello-world


