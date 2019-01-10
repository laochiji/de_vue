pipeline {
    agent none
    stages {
        stage('Non-Parallel Stage') {
			agent {
				label "slave1"
			}
            steps {
                echo 'This stage will be executed first.'
            }
        }
		stage('Test') { 
			agent {
				label "slave1"
			}
			steps {
                echo 'This stage will be executed 2th.'
            }	
		}
        stage('Parallel Stage') {
            parallel {
                stage('build1') {
				agent {
                        label "master"
                    }
                    steps {
                        echo "On Branch A"
						build job: 'test1'
                    }
                }
                stage('build2') {
                    agent {
                        label "master"
                    }
                    steps {
                        echo "On Branch B"
						build job: 'test2'
                    }
                }
				stage('build3') {
                    agent {
                        label "master"
                    }
                    steps {
                        echo "On Branch B"
						build job: 'test3'
                    }
                }
            }
        }
    }
}