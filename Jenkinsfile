node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage("prepare container"){
         sh ' docker rm -f $(docker ps -a -f name=dockerreact_v1 -q)'
    }

    stage('Build image test') {
        app = docker.build("dockerreact_v1","-f Dockerfile.dev .")
       
    }   

    stage('test image') {
        sh 'docker run --name=dockerreact_v1 -d -p 3000:3000  dockerreact_v1 npm run test'
    }

    
}
