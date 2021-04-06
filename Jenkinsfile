pipeline {
    agent none
    stages {
        stage("Build") {
            agent {
                docker { image 'node:14.16.0-alpine3.13' }
            }
            steps {
                sh "yarn install"
                sh "yarn build"
            }
        }
        stage("Deploy") {
            agent {
                docker { image 'node:14.16.0-alpine3.13' }
            }
            steps {
                sh "sudo rm -rf /var/www/jenkins-react-app"
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
            }
        }
    }
}
