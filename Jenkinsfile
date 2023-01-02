pipeline {
      agent any
      stages {
        stage('Maven Compile'){
        steps{
            echo 'Project compile stage'
            bat label: 'Compilation running', script: '''mvn compile'''
          }
    }

    stage('Unit Test') {
      steps {
        echo 'Project Testing stage'
        bat label: 'Test running', script: '''mvn test'''
        }
    }

    stage('Jacoco Coverage Report') {
        steps{
            jacoco()
        }
    }

    stage('Jacoco'){
        steps{
            jacoco()
        }

    }

    stage('Generate Cucumber report') {
            steps{
                 cucumber buildStatus: 'UNSTABLE',
                      reportTitle: 'My Cucumber Report',
                      fileIncludePattern: '**/*.json',
                         trendsLimit: 10,
                      classifications: [
                          [
                              'key': 'Browser',
                              'value': 'Chrome'
                          ]
                      ]
                  }
         }

            
            
   stage('SonarQube'){

steps{

bat label: '', script: '''mvn sonar:sonar \

-Dsonar.host.url=http://localhost:9000 \

-Dsonar.login=squ_572d81ff354cf46f297fc735733958f7f836a66f'''

}

   } 
    
   
            
            

    stage('Maven Package'){
    steps{
        echo 'Project packaging stage'
        bat label: 'Project packaging', script: '''mvn package'''
        }
    } 
  }
}
