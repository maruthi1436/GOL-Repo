pipeline {
    agent any 
    tools { 
        maven 'Maven' 
      
    }
stages { 
     
 //stage('Preparation') { 
 //   steps {
// for display purpose

      // Get some code from a GitHub repository

<<<<<<< HEAD
   //  git 'https://github.com/raknas999/GOL-Repo.git'
=======
      //git 'https://github.com/raknas999/game-of-life.git'
      git 'https://github.com/raknas999/GOL-Repo.git'
>>>>>>> 3720fc23a2b108e80eca96dd19a21044ab5a9eac

      // Get the Maven tool.
     
 // ** NOTE: This 'M3' Maven tool must be configured
 
     // **       in the global configuration.   
     //}
   //}

   stage('Build') {
       steps {
       // Run the maven build

      //if (isUnix()) {
         sh 'mvn -Dmaven.test.failure.ignore=true install'
      //} 
      //else {
      //   bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
       }
//}
   }
 
  stage('Unit Test Results') {
      steps {
      junit '**/target/surefire-reports/TEST-*.xml'
      
     }
 }
  stage('Sonarqube') {
    environment {
        def scannerHome = tool 'sonarqube';
    }
    steps {
      withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
            
        }
<<<<<<< HEAD
    //    timeout(time: 10, unit: 'MINUTES') {
    //      waitForQualityGate abortPipeline: true
    //    }
=======
        timeout(time: 10, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
>>>>>>> 3720fc23a2b108e80eca96dd19a21044ab5a9eac
    }
}
     stage('Artifact upload') {
      steps {
<<<<<<< HEAD
     nexusPublisher nexusInstanceId: '1234', nexusRepositoryId: 'releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'gameoflife-web/target/gameoflife.war']], mavenCoordinate: [artifactId: 'gameoflife', groupId: 'com.wakaleo.gameoflife', packaging: 'war', version: '$BUILD_NUMBER']]]
=======
       nexusPublisher nexusInstanceId: '1234', nexusRepositoryId: 'releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'gameoflife-web/target/gameoflife.war']], mavenCoordinate: [artifactId: 'gameoflife', groupId: 'com.wakaleo.gameoflife', packaging: 'war', version: '$BUILD_NUMBER']]]
>>>>>>> 3720fc23a2b108e80eca96dd19a21044ab5a9eac
      }
     }
    stage('Deploy War') {
      steps {
          //deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', url: 'http://18.220.134.203:8080/')], contextPath: null, war: '**/*.war'
          sh label: '', script: 'ansible-playbook deploy.yml'
      }
 }
}
post {
       success {
            archiveArtifacts 'gameoflife-web/target/*.war'
        }
<<<<<<< HEAD
        failure {
            mail to:"raknas000@gmail.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Build failed"
=======
       failure {
           mail to:"raknas000@gmail.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Build failed"
>>>>>>> 3720fc23a2b108e80eca96dd19a21044ab5a9eac
        }
    }       
}
