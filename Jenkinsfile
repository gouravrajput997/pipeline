node {
	/* Continuous integration (CI), continuous delivery (CD) and continous Deployment */
    def cicdpipeline

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace /var/lib/jenkins/workspace/jobname*/

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image from Docker File */

        cicdpipeline = docker.build("mitrasonu/cdw")
    }

    stage('Test image') {
        
        cicdpipeline.inside {
            echo "Tests Passed Continous Delivery to Docker push"
        }
    }

    stage('Push image') {
        /* You would need to first register with DockerHub before you can push images to your account */
        docker.withRegistry('https://registry.hub.docker.com', 'docker') {
            cicdpipeline.push("${env.BUILD_NUMBER}")
     } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}
