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
                sh 'chmod +x mvnw'
                sh './mvnw clean:clean'
                sh './mvnw dependency:copy-dependencies'
                sh './mvnw compiler:compile'
            }
        }
        stage('Package'){
            steps{
                sh './mvnw -B -DskipTests package --no-transfer-progress'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts allowEmptyArchive: true,
                    artifacts: 'target/*.jar, target/*.war'
            }
        }
    }
}

