# ArgoCD
Installing ArgoCD in Jenkins DOcker K8s Pipeline for a multitier springapp deployment

Ticket2: Installing Jenkins to runc docker command with an iAM role attached.
==============================================================================
1. starts with sudo apt update
2. First Install docker
	sudo apt install docker.io -y
	sudo systemctl start docker
	sudo systenctl enable docker.service

3. Install and configure Jenkins
	first Install Java
	
	sudo apt install openjdk-17-jre
	java -version

	curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
 echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

	sudo apt-get update
	sudo apt-get install jenkins

4. Start Jenkins, 
	sudo systemctl start jenkins

5. Add jenkins user to docker group so jenkins can execute docker command

	usermod -aG docker jenkins 
6. Restart docker.
	sudo systemctl restart docker.service

7. Add jenkins to sudoer grp so jenkin can perform admin tasks	
		sudo echo " jenkins ALL= (ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/jenkins 

4.  Check jenkins shell if its binbash, if not change false to binbash on root
		sudo vi /etc/passwd

9. Switch to Jenkins
	sudo su - jenkins


5. check that Jenkins can run docker commands
	 docker ps
