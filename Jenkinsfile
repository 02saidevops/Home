pipeline{
    agent any
    tools{
        maven 'Maven'
    }
    stages{
        stage("GitHub"){
            steps{
                git 'https://github.com/02saidevops/Home.git'
            }
        }
        stage("Build-Maven"){
            steps{
                sh "mvn clean install package"
            }
        }
        stage("Deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://54.146.141.98:8090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
