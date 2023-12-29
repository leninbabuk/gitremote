pipeline {
    agent any
    
      tools{
        maven 'Maven'
    }

    stages {
        stage('GitPull') {
            steps {
                git credentialsId: 'githubuser', url: 'https://github.com/leninbabuk/gitremote.git'
            }
        }
    
    

        stage('Build') {
            steps {
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Push artifacts into artifactory') {
            steps {
              rtUpload (
                serverId: 'jfrog',
                spec: '''{
                      "files": [
                        {
                          "pattern": "*.jar",
                           "target": "myrepo"
                        }
                    ]
                }'''
              )
          }
        }
    
    
    
    
    }

}     
