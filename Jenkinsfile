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
		stage('MakeDJangoMigrations') {
			steps {
				sh '''bash -c "cd PRUEBA/ && python3 manage.py makemigrations"'''
			}
		}
		stage('MigrateToDatabase') {
			steps {
				sh '''bash -c "cd PRUEBA/ && python3 manage.py migrate"'''
			}
		}
		stage('TestApp') {
			steps {
				sh '''bash -c "cd PRUEBA/ && python3 manage.py test"'''
			}
		}
	}
}


















