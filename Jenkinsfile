pipeline {
	
    agent any
	
	triggers {
		if (env.BRANCH_NAME == "master") {
			cron('@hourly')
		} else {
			// Run on a manual basis
		}
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