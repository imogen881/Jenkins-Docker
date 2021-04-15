pipeline{
        agent any
        stages{
            stage('Install Docker'){
                steps{
                    sh '''sudo apt update -y
			sudo apt install curl -y
			curl https://get.docker.com | sudo bash
			sudo usermod -aG docker $(whoami)
			version=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r '.tag_name')
			sudo curl -L "https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
			sudo chmod +x /usr/local/bin/docker-compose'''
                }
            }
	stage('Deploy'){
	steps{
	sh "sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d"
	}
}
}
}
