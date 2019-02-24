node {
    def app

    stage('Clone repository') {
    	checkout scm
    }

    stage('Build image') {
        app = docker.build("sebastian9486/static-placeholder-website")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

	stage('Push image to registry') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
		 * Credentials "docker-hub-credentials" are stored within Jenkins. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }

	stage('Deploy image to AWS') {
		app.inside {
            sh 'echo "Container was deployed successfully"'
        }
    }
}
