pipeline {
    agent any
    stages {
        stage("build") {
            steps {
                snDevOpsStep()
                checkout scm
                sh 'ng build'
            }
        }
        stage("unit test") {
            steps {
                snDevOpsStep()
            
                sh 'ng test'
            }
            post {
       		   always {
          		    junit '**/build/reports/e2e/*.xml'
        	    }
            }
        } 
        stage("e2e test") {
            steps {
                snDevOpsStep()
                sh 'ng serve'
                sh 'ng e2e'
            }
            post {
       		   always {
          		    junit '**/build/reports/e2e/*.xml'
        	    }
            }
        }      
    }    
}
