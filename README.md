## Installation

##### 1. Install docker and docker-compose:

  - Mac: Download the installer from [Docker](https://store.docker.com/editions/community/docker-ce-desktop-mac)
   
  - Linux:
  
    - Uninstall old versions
    
        `sudo apt-get remove docker docker-engine docker.io`
        
    - Update the apt package index:
      
        `sudo apt-get update`
        
    - Install packages to allow apt to use a repository over HTTPS:
    
        `sudo apt-get install \
            apt-transport-https \
            ca-certificates \
            curl \
            software-properties-common`
          
    - Add Docker’s official GPG key:
      
        `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
        
    - Add Docker repository:
    
        `sudo add-apt-repository \
            "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
            $(lsb_release -cs) \
            stable"`
            
    - Install Docker CE:
    
        - Update the apt package index:
        
            `sudo apt-get update`
            
        - Install the latest version of Docker CE, or go to the next step to install a specific version:
        
            `sudo apt-get install docker-ce docker-compose`
        
    - To make docker run without sudo execute:

        - Create the docker group if it doesn't already exist:
    
            `sudo groupadd docker`
        
        - Add your user to the docker group:
    
            `sudo usermod -aG docker $USER`
        
        - Logout and login again    

##### 2. Setup environment parameters:

  - Copy the default docker-compose configuration and give custom values to the variables in the file.
  
        cp ./docker-compose.override.yml.dist ./docker-compose.override.yml   
    
##### 3. Create the images and run the containers executing:
    
    docker-compose up -d
        
##### 4. Run the webapp:

Load [http://localhost](http://localhost) on your browser

##### 5. Generate Certbot Certificates:

Execute this command on the server, not inside the containers:

    certbot certonly --webroot -w /var/www/alex-agile-blog/public -d www.alexbarbacoaching.com -w /var/www/alex-agile-blog/public -d alexbarbacoaching.com -w /var/www/alex-agile-blog/public -d expanding-leadership.alexbarbacoaching.com

##### 6. Renew Certbot Certificates:

    certbot renew