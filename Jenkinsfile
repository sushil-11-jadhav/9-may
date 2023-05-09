pipeline {
	agent {
				label {
					label "slave"
					customWorkspace "/mnt/slj"
				}
			}
	stages {
		stage ("docker started") {
			steps {
				sh "service docker start"
				
			}
		}		
		stage ("docker httpd run on slave") {	
			steps {
					sh "rm -rf /mnt/slj/*"
					sh "docker kill server2"
					sh "docker system prune -a -f"
					sh "service docker start"
					sh "rm -rf /mnt/slj/*"
					sh "docker run -dp 90:80 --name server2 httpd"
					sh "git clone https://github.com/sushil-11-jadhav/9-may.git -b 23Q2"
					sh "chmod -R 777 /mnt/slj/9-may/index.html"
					sh "docker cp /mnt/slj/9-may/index.html server2:/usr/local/apache2/htdocs"
			}
		}
	}
}	
