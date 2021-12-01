pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: maven
    image: maven:3.6.3-jdk-8-openj9
    command:
    - cat
    tty: true
"""
   }}
  parameters {
    string(name: 'BRANCH_NAME', defaultValue: 'master', description: '')
  }
   stages {
      stage('Hello-1') {
         steps {
            container('maven') {
              sh "echo `date` >> newfile.txt"
            }
         }
      }
   }
   post {
    success {
        archiveArtifacts 'newfile.txt'
    }
  }
}
