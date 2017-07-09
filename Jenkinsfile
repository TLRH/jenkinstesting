String cron_string = BRANCH_NAME == "master" ? "@hourly" : ""

pipeline {
	
    agent any
	
	triggers {
		//cron("H/5 * * * *")
	}

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GitHub', url: 'https://github.com/TLRH/jenkinstesting.git']]])
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}