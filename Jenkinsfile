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
                awsCodeDeploy(
                    applicationName: 'JenkinsCodeDeployApp',
                    deploymentGroupName: 'JenkinsDeploymentGroup',
                    deploymentConfig: 'CodeDeployDefault.OneAtATime',
                    region: 'ap-south-2',
                    s3bucket: 'YOUR_BUCKET_NAME',
                    s3prefix: 'deploy'
                )
            }
        }
    }
}
