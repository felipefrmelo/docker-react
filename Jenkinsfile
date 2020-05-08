
node {

    def app

    stage('Clone repository') {
        checkout scm
    }

    stage("prepare container"){
         sh ' docker rm -f $(docker ps -a -f name=dockerreact_v1 -q)'
    }

    stage('Build image tesoit') {
        app = docker.build("dockerreact_v1","-f Dockerfile.dev .")
       
    }   

    stage('test image') {
        sh 'docker run --name=dockerreact_v1 -d --rm dockerreact_v1 npm run test'
        sh 'docker rm -f $(docker ps -a -q -f name=dockerreact_v1)'
    }

    stage('deploy') {
        app2 = docker.build('react-app')
    
        sh 'docker run --name=dockerreact_v1 -p 3000:80 dockerreact_v1'
    }

    
}
