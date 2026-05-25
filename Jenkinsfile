pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Amrue320/jenkins-codedeploy-demo.git'
            }
        }

        stage('Deploy to CodeDeploy') {
            steps {
                step([
                    $class: 'AWSCodeDeployPublisher',
                    applicationName: 'amruthesh-JenkinsCodeDeployApp',
                    deploymentGroupName: 'amruthesh-JenkinsDeploymentGroup',
                    deploymentConfig: 'CodeDeployDefault.AllAtOnce',
                    region: 'ap-south-2',
                    s3bucket: 'amruthesh-bucket',
                    s3prefix: 'deploy'
                ])
            }
        }
    }
}
