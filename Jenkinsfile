pipeline {
   agent { 
        node {
            label 'docker-merde'
            }
      }

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building..."
                dir('myapp') {
                    sh 'pip install --break-system-packages -r requirements.txt'
                }
            }
        }

        stage('Test') {
            steps {
                echo "Testing..."
                dir('myapp') {
                    sh '''
                        python3 hello.py
                        python3 hello.py --name=Brad
                    '''
                }
            }
        }

        stage('Deliver') {
            steps {
                echo 'Delivering...'
                sh 'echo "Doing delivery stuff..."'
            }
        }
    }
}
