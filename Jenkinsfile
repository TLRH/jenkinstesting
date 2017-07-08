pipeline {
	
    agent any
	
	if (env.BRANCH_NAME.contains("master") {
		properties([
		  buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '30')),
		  disableConcurrentBuilds(),
		  overrideIndexTriggers(true),
		  pipelineTriggers([cron('@hourly')])
		])
	} else {
		properties([
		  buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '30')),
		  disableConcurrentBuilds(),
		  overrideIndexTriggers(true),
		  pipelineTriggers([])
		])
	}

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GitHub', url: 'https://github.com/TLRH/jenkinstesting.git']]])
				echo 'Change Sets are as follows'
				echo currentBuild.changeSets
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