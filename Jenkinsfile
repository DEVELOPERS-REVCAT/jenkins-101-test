pipeline { 
    agent {        
        docker { 
            image 'python:3' // Specify the Docker image
            label 'docker-agent-python'            
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
     environment {
        PATH = "/usr/bin:$PATH"  // Add /usr/bin to the PATH
    }
    stages { 
        stage('Build') {
            steps {
                
                withPythonEnv('/usr/bin/python3.9') {
                    sh 'echo "Job is starting" '
                    echo "Building.."
                    sh '''
                    cd myapp
                    ls -la
                    #!/bin/bash
                    echo $PATH
                    echo $HOME
                    pip3 install -r requirements.txt
                    '''    
                }    
            }            
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}
