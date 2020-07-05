node {

    def app

    environment {
        registry = 'myhk2009/sample-microservices'
        registryCredential = 'dockerhubCredentials'
        VERSION_NUMBER = '1.0.0'
    }

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
        sh 'echo "Start Clone"'
        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        sh 'echo "Start Build"'
        app = docker.build('myhk2009/sample-microservices')
    }


    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhubCredentials') {
            app.push("1.0.0")
            app.push("latest")
        }
    }
}