node{
	stage('SCM Checkout'){
		git branch: 'wartomcat', url: 'https://github.com/soulunstable/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven-3', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploy to Tomcat'){
		sshagent(['pem-tomcatser']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@13.59.207.93:/opt/tomcat9/webapps/'
	}
	}
	stage('Email Notification'){
	mail bcc: '', body: 'Deployed to tomcat', cc: '', from: 'adhikarimay@gmail.com', replyTo: 'adhikarimay@gmail.com', subject: 'This is Subject', to: 'adhikarimay@gmail.com'
	}

}
