pipeline {
	agent {
				label {
					label "slave ssh"
					customWorkspace "/mnt/sls"
				}
			}
	stages {
		stage ("docker started") {
			steps {
				sh "service docker start"
				
			}
		}		
		stage ("docker httpd run on slave ssh") {	
			steps {
					sh "sudo rm -rf /mnt/sls/*"
					sh "sudo docker kill server3"
					sh "sudo docker system prune -a -f"
					sh "sudo service docker start"
					sh "sudo rm -rf /mnt/sls/*"
					sh "sudo docker run -dp 8081:80 --name server3 httpd"
					sh "sudo git clone https://github.com/sushil-11-jadhav/9-may.git -b 23Q3"
					sh "sudo chmod -R 777 /mnt/sls/9-may/index.html"
					sh "sudo docker cp /mnt/sls/9-may/index.html server3:/usr/local/apache2/htdocs"
			}
		}
	}
}
