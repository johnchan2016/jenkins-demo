node {

    //def app

/*     environment {
        registry = 'myhk2009/sample-microservices'
        registryCredential = 'dockerhubCredentials'
        VERSION_NUMBER = '1.0.0'
        REPO= 'github.com/johnchan2016/jenkins-demo.git'
    } */

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
        dir("jenkins-demo") {
            withCredentials([usernamePassword(credentialsId: 'gitHubCredentials', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                script {
                    env.encodedPass=URLEncoder.encode(GIT_PASSWORD, "UTF-8")
                }
                
                sh 'ls'
                sh 'git config --global user.name "johnchan"'
                sh 'git config --global user.email myhk2009@gmail.com'
                sh 'echo "Added another line to REAMD.md" >> README.txt'
                sh 'git status'
                sh 'git add .'
                sh "git commit -m 'Jenkins'"
                //sh 'git remote add origin https://${GIT_USERNAME}:${encodedPass}@github.com/johnchan2016/jenkins-demo.git'
                sh 'git push -u origin master'
            }
        }
    }

/*     stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhubCredentials') {
            app.push("1.0.0")
            app.push("latest")
        }
    } */
}