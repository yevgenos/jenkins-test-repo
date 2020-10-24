pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Deploy') {
            steps {
                retry(3) {
                    sh './flakey-deploy.sh'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh './health-check.sh'
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Fail!; exit 1'
            }
        }
        post{
            always{
                echo 'This will always run'
            }
            success{
                echo 'This will only run when successful'
            }
            failure{
                echo 'This will only run when failed'
            }
            unstable{
                echo 'This will only run if the build is unstable'
            }
            changed{
                echo 'This will run if a stage of the build has changed'
                echo 'For example, pipeline was previously failing but now succeding'
            }
        }
    }
}
