node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
        sh "git clone https://github.com/johankcarlsson/docker-flask-gunicorn-test.git"
        //checkout scm
        sh "pwd"
        sh "ls -lrt *"
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
         sh "cd myapp"
         sh "pwd"
         sh "ls -lrt"
         sh "docker build -t flask-test:1.3 ."

        //app = docker.build("getintodevops/hellonode")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        /*app.inside {
            sh 'echo "Tests passed"'
        }*/
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        /*docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }*/
    }
    post {
        cleanup {
            /* clean up our workspace */
            deleteDir()
            /* clean up tmp directory */
            dir("${workspace}@tmp") {
                deleteDir()
            }
            /* clean up script directory */
            dir("${workspace}@script") {
                deleteDir()
            }
        }
    }
}
