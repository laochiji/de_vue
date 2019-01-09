pipeline {
    agent any
    stages {
        stage('Non-Parallel Stage') {
            steps {
                echo 'This stage will be executed first.'
            }
        }
		stage('Test') { 
			agent {
				label "slave1"
			}
			steps {
                echo 'This stage will be executed first.'
				build "test"
            }	
		}
        stage('Parallel Stage') {
            parallel {
                stage('build1') {
                    steps {
                        echo "On Branch A"
						build "test1"
                    }
                }
                stage('build2') {
                    agent {
                        label "master"
                    }
                    steps {
                        echo "On Branch B"
						build "test2"
                    }
                }
				stage('build3') {
                    agent {
                        label "master"
                    }
                    steps {
                        echo "On Branch B"
						build "test"
                    }
                }
            }
        }
    }
}
