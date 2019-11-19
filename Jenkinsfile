pipeline {
    agent any

    stages {
        stage('Testing Environment') {
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
    }
}

