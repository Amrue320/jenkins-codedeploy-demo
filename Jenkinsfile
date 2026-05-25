pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/YOUR_USERNAME/jenkins-codedeploy-demo.git'
            }
        }

        stage('Deploy to CodeDeploy') {
            steps {
                awsCodeDeploy(
                    applicationName: 'JenkinsCodeDeployApp',
                    deploymentGroupName: 'JenkinsDeploymentGroup',
                    deploymentConfig: 'CodeDeployDefault.OneAtATime',
                    region: 'ap-south-1',
                    s3bucket: 'your-s3-bucket',
                    s3prefix: 'deploy'
                )
            }
        }
    }
}
