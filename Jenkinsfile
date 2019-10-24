pipeline {
    agent any 
    stages {
    stage ('pull'){
        steps {
            git credentialsId: 'github', url: 'https://github.com/oselukar/vue-starter.git'
            sh 'echo "This pipeline is build from production branch"'
        } 
                   }
        stage ('analysis'){
            steps  { 
                 sh 'docker container run --rm -v /home/ubuntu/.jenkins_testbed/workspace/$JOB_NAME:/app/ ajitemsahasrabuddhe/sonar-scanner:13 -Dsonar.projectBaseDir=/app/'
                    }
                          }
 
 stage ('Docker-Build') {
     steps {
         sh 'docker build -t omkesh/vue-starter:v${BUILD_NUMBER}-${GIT_BRANCH} .'    
           }
 }
stage ('docker push'){
     steps { 
         withDockerRegistry([credentialsId: 'dockerhub' , url: ""]){    
             sh 'docker push omkesh/vue-starter:v${BUILD_NUMBER}-${GIT_BRANCH}'
                                                                   }        
            }
                    }
            }           
        }
