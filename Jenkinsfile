node{
	stage('SCM Checkout'){
		git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven-3', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#devops', color: '439FE0', message: 'Build successed', teamDomain: 'devops-dxa2539', tokenCredentialId: 'slack-secret'

	}

}
