pipeline {
    agent any
    environment {
    ANYPOINT_CORP = credentials('cloud_cred')
 }
 parameters {
        string(name: 'businessGroup', defaultValue: '', description: 'Business Group To Deploy')
        string(name: 'environment', defaultValue: '', description: 'Environment')
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Staring to deploy using Jenkins Credentials.....'
                sh "mvn deploy -DmuleDeploy -Dusername=$ANYPOINT_CORP_USR -Dpassword=$ANYPOINT_CORP_PSW -DbusinessGroup=${params.businessGroup} -Denvironment=${params.environment}"
            }
        }
      
    }
 }