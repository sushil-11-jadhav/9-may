pipeline {
	agent {
		label {
			label "built-in"
			customWorkspace "/mnt/welcome"
		}
	}
	stages {
		stage ("docker started") {
			steps {
				sh "service docker start"
				
			}
		}		
		stage ("docker httpd run on JM") {
			steps {
					sh "rm -rf /mnt/welcome/*"
					sh "docker kill server1"
					sh "docker system prune -a -f"
					sh "docker run -dp 80:80 --name server1 httpd"
					sh "git clone https://github.com/sushil-11-jadhav/9-may.git -b 23Q1"
					sh "chmod -R 777 /mnt/welcome/9-may/index.html"
					sh "docker cp /mnt/welcome/9-may/index.html server1:/usr/local/apache2/htdocs"
			}
		}
	}
}	
