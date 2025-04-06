pipeline { 
    agent any  // Use any available agent 
 
    tools { 
        maven 'Maven'  // Ensure this matches the name configured in Jenkins 
    } 
    stages { 
        stage('Checkout') { 
            steps { 
                git 'https://github.com/dish3045/mavenjenkinspipeline.git' 
            } 
        } 
 
        stage('Build') { 
            steps { 
                sh 'mvn clean package'  // Run Maven build 
            } 
        } 
 
        stage('Archive') { 
            steps { 
                archieveArtifacts artifacts 'target/*.war', fingerprint:true 
            } 
        } 
 
 stage('Deploy') { 
            steps { 
                sh 'mvn clean package'   
            } 
        }     
               
    } 
 
    post { 
        success { 
            echo 'Build and deployment successful!' 
        } 
        failure { 
            echo 'Build failed!' 
        } 
    } 
}
