pipeline {
    agent any

    triggers {
        githubPush() // This enables GitHub webhook trigger
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Iammksharma5/cicdprocess.git'
            }
        }

        stage('Trigger Freestyle Jobs') {
            steps {
                script {
                    def jobs = ['Project-1', 'Project-2', 'Project-3', 'Project-4', 'Project-5']
                    
                    for (job in jobs) {
                        echo "Triggering Job: ${job}"
                        def result = build job: job, wait: true, propagate: true
                        echo "${job} completed with status: ${result.getResult()}"
                    }
                }
            }
        }
    }

    post {
        success {
            echo "All jobs executed successfully!"
        }
        failure {
            echo "One or more jobs failed."
        }
    }
}

