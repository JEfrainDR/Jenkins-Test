pipeline {
	agent any
	stages {
		stage('Checkout') {
			steps {
				git poll: true, url:'https://github.com/JEfrainDR/Jenkins-Test.git'
			}
		}
		stage('CreateVirtualEnv') {
			steps {
				sh '''bash -c "virtualenv env && source env/bin/activate"'''
			}
		}
		stage('InstallRequirements') {
			steps {
				sh '''bash -c "source ${WORKSPACE}/env/bin/activate && ${WORKSPACE}/env/bin/python ${WORKSPACE}/env/bin/pip install -r requirements.txt"'''
			}
		}
		stage('TestApp') {
			steps {
				sh '''cd newproject/ && python3 manage.py runserver'''
				
			}
		}
		stage('RunApp') {
			steps {
				sh '''bash -c "source env/bin/activate ; ${WORKSPACE}/env/bin/python src/main.py &"'''
			      }
		}
		stage('BuildDocker') {
			steps {
				sh '''sudo -u root -p JEfrainDR314602820300 docker build ${WORKSPACE}/DockerFiles/'''
			      }
		}
		stage('PushDockerImage') {
			steps {
				sh '''docker tag apptest:latest mijack/apptest:latest
					docker push mijack/apptest:latest
					docker rmi apptest:latest'''
			}
		}
	}
}


















