pipeline {
    agent { label "Jenkins_slave" }
    stages {
        stage('Gitclone') {
            steps {
                git 'https://github.com/madhavivijay/hello-world-webapp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true clean package'
                echo 'Building the project...'
                // commands to build the project
            }
        }
        stage('TomcatDeploy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'Tomcat_login', path: '', url: 'http://3.109.181.21:8080')], contextPath: null, war: '**/*.war'
                echo 'Deploying to production...'
                // commands to deploy to production
            }
        }
        stage('Monitor') {
            steps {
                echo 'Monitoring the production environment...'
                // commands to monitor the production environment
            }
        }
    }
}
