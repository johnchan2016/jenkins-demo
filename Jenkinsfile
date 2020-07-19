pipeline {

    def app

    environment {
        registry = 'myhk2009/sample-microservices'
        registryCredential = 'dockerhubCredentials'
        VERSION_NUMBER = '1.0.0'
    }

/*     stage('Clone repository') {
        sh 'echo "Start Clone"'
        checkout scm
    } */

/*     stage('Build image') {
        sh 'echo "Start Build"'
        app = docker.build('myhk2009/sample-microservices')
    } */


/*     stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    } */

    stage('git push') {
        withCredentials([usernamePassword(credentialsId: 'githubCredentials', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
            sh 'REPO=https://github.com/johnchan2016/jenkins-demo.git'
            sh 'git clone ${REPO}'
            sh 'echo "Added another line to REAMD.md" >> README.md'
            sh("git tag -a some_tag -m 'Jenkins'")
            sh('git push https://${GIT_USERNAME}:${GIT_PASSWORD}@${REPO} --tags')
        }
    }

/*     stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhubCredentials') {
            app.push("1.0.0")
            app.push("latest")
        }
    } */
}