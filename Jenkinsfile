pipeline {
   agent any
   stages {
      stage('SCM') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/sri008/Trading-UI.git'
         }
      }
      stage('Build') {
         steps {
            sh '''
            npm install
            ng build --base-href=/Matrimony/
            '''
          }
       }
      stage('Deploy') {
         steps {
            sh '''
            cp -r $WORKSPACE/Matrimony /opt/apache-tomcat-9.0.35/webapps
            curl -u admin:admin http://18.232.53.211:8888/manager/reload?path=/Matrimony
            '''
         }
      }
   }
}
