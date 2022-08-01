pipeline {
    
    agent any

    options {
        timestamps ()
    }

    stages {

        stage('Checkout Stage') {
            steps {
                git branch: env.BRANCH,
                url: 'https://github.com/i-kozak/cicd.git'
            }
        }

        stage('Parallel Execution') {
            parallel {
                stage('Docs Stage') {
                    steps {
                        echo "it is docs stage"
                        //sh "tox -e docs"
                    }
                }

                stage('Linters Stage') {
                    steps {
                        echo "it is linters stage"
                        //sh "tox -e linters"
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
