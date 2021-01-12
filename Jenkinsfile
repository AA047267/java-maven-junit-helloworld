def sonar_analysis_publish(){
     sh 'mvn clean install sonar:sonar -Dsonar.host.url=https://sonar.mediaiqdigital.com/sonar/  -Dsonar.analysis.mode=publish -Dsonar.junit.reportPaths=target/surefire-reports -Dsonar.java.coveragePlugin=jacoco -Dsonar.jacoco.reportPaths=target/coverage-reports/jacoco-ut.exec -Dsonar.inclusions=**/*.kt,**/*.java -Dsonar.java.binaries=**/classes/** -Dsonar.login=${SonarToken} -Dsonar.password='
}

pipeline {    

       agent any
       stages {
         stage('clean-workspace') {
            steps {
                script {
                    cleanWs()
                }
            }
         }
         
           
         stage("build & SonarQube analysis") {
           tools {
              jdk 'JAVA8' 
           }
           steps {
            script {
                sonar_analysis_publish()
            }
           }
         }

       }
}
