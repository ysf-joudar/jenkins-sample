// Powered by Infostretch 

timestamps {

node () {

	stage ('App-IC - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git-login', url: 'https://github.com/ysf-joudar/jenkins-sample.git']]]) 
	}
	stage ('App-IC - Build') {
 			// Maven build step
	withMaven(maven: 'Maven-3') { 
 			if(isUnix()) {
 				sh "mvn clean package " 
			} else { 
 				bat "mvn clean package " 
			} 
 		} 
	}
	stage ('App-IC - Post build actions') {
/*
Please note this is a direct conversion of post-build actions. 
It may not necessarily work/behave in the same way as post-build actions work.
A logic review is suggested.
*/
		// Mailer notification
		step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: 'youssef.joudar@adserviolyon.fr', sendToIndividuals: false])
 
	}
}
}