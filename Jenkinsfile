pipeline{
        agent any
        stages{
            stage('Clone repo'){
                steps{
                    sh "git clone https://gitlab.com/qacdevops/chaperootodo_client"
                }
            }
            stage('Install Docker'){
                steps{
                    sh "curl https://get.docker.com | sudo bash"
                }
            }
	    stage('Install Docker Compose'){
	    	steps{
			sh "sudo curl -L "https://github.com/docker/compose/releases/download/1.29.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose"
			sh "sudo chmod +x /usr/local/bin/docker-compose"
			sh "export DB_PASSWORD="password"
		}
       	}
	stage('Deploy'){
	steps{
	sh "sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d"
	}
}
}
