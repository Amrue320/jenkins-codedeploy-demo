pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'ap-south-2'
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Amrue320/jenkins-codedeploy-demo.git'
            }
        }

        stage('Deploy to CodeDeploy') {
            steps {

                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'jenkins'
                ]]) {

                    sh '''
                    zip -r deploy.zip appspec.yml index.html scripts

                    aws deploy push \
                    --application-name amruthesh-JenkinsCodeDeployApp \
                    --s3-location s3://amruthesh-bucket/deploy.zip \
                    --ignore-hidden-files

                    aws deploy create-deployment \
                    --application-name amruthesh-JenkinsCodeDeployApp \
                    --deployment-group-name amruthesh-Jenkins-deployement-group \
                    --deployment-config-name CodeDeployDefault.AllAtOnce \
                    --s3-location bucket=amruthesh-bucket,key=deploy.zip,bundleType=zip
                    '''
                }
            }
        }
    }
}