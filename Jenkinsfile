pipeline {
    agent any
    environment {
    VERSION = readMavenPom().getVersion()
    }
    stages {
               /stage('version'){
                    steps{
                        echo "${VERSION}"
                    }
                }
                stage('Test Environment') {
                    steps {
                            sh 'mvn test -Dtest=ControllerAndServiceSuite'
                    sh 'mvn test -Dtest=IntegrationSuite'
                        }
                }
                stage('Build') {
                    steps {
                echo "Build"
                sh 'mvn package -DskipTests'
                sh 'docker build -t="moam97/simple-project-server:latest" .'
                        }
                }
                stage('Deploy') {
                    steps {
                echo "Deploy"
                sh 'docker push moam97/simple-project-server:latest'            
                    }
                }
                stage('Testing Environment') {
                    steps {
                        echo "hello"
                    }
                }
                stage('Staging') {
                     when{ 
                            expression{
                                env.BRANCH_NAME=="master"
                            }
                        }
                    steps {
                        echo "hello"
                    }
                }
                stage('Production') {
                        when{ 
                            expression{
                                env.BRANCH_NAME=="master"
                            }
                        }
                        steps {
                            echo "hello"
                        }
                }

    }
}

