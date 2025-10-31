pipeline{
    agent any
    tools{
        git 'Default'
    }
    stages{
        stage("GetProject"){
            steps {
                git branch:'main', url:'https://github.com/FionnSlattery/Spring_Boot_2.git'
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean:clean'
                sh 'mvn dependency:copy-dependencies'
                sh 'mvn compiler:compile'
            }
        }
        stage('Package'){
            steps{
                sh 'mvn package'
            }
        }
    }
    stage ('Archive') {
        steps {
            archiveArtifacts allowEmptyArchive: true,
                artifacts: '**/demo*.war'
        }
    }
}
