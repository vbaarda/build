pipeline {
	agent none
	environment {
		NODE_VER = '8.1.0'
	}
	stages {
		stage('Beginning') { agent any
			environment {
				NEW_VAR = 'Howdy!'
			}
			steps {
				echo 'Hello world'
				sh 'echo $NODE_VER'
				echo "${env.NEW_VAR}"
			}
		}
	
		stage('Who am I?') { agent any
			steps {
				echo "${env.NEW_VAR}"
				sh 'host -t TXT pgp.michaelholley.us | awk -F \'"\' \'{print $2}\''
			}
		}
		stage('Deploy to stage?') {agent none
			steps {
				input 'Deploy to stage?'
			}
		}
		stage('Parallel') { agent any 
			failFast true
			parallel {
				stage('Build 1') {
					echo "It's ME!"

				}
				stage('Build 2')  {
					echo "It's not me!"
				}
			}
		}
	}
}
