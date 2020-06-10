pipeline {
   agent any
   stages {
      stage('SCM') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/sri008/Kalyanam-UI.git'
         }
      }
      stage('Build') {
         steps {
            sh '''
            npm install
            ng build --base-href=/matrimony/
            '''
          }
       }
      stage('Deploy') {
         steps {
            sh '''
            cp -r $WORKSPACE/matrimony /opt/apache-tomcat-9.0.36/webapps
            curl -u admin:admin http://35.170.73.70:8888/manager/reload?path=/matrimony
            '''
         }
      }
   }
}
