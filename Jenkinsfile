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
				sh '''bash -c "pip3 install -r requirements.txt"'''
			}
		}
		stage('MakeMigrations') {
			steps {
				sh '''bash -c "cd newproyect/ && python manage.py migrate"'''
				
			}
		}
	
	}
}


















