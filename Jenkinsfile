node {
   def mvnHome
   stage('Preparation') { // for display purposes
   
   checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'a9ee3dc3-1073-4e39-8f74-31c6fb6ec4cd', url: 'https://github.com/honeysundar/java_application.git']]])
   
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
          sh returnStatus: true, script: 'mvn install'

       //  sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('deploy') {
    build 'deployment_job'   
   }
   
}
