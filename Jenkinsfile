node {
    def app

    stage('Clone repository') {
        checkout scm
    }


    stage('Build image') {
        app = docker.build("dockerreact_v1")
    }

    stage('Deploy') {
        sh 'docker run --name=dockerreact_v1 -d -p 3000:3000 -p 8081:8081 dockerreact_v1'
    }

    stage("deploy"){
        steps{
            echo "====++++executings deploy++++===="
        }
        post{
            always{
                echo "====++++always++++===="
            }
            success{
                echo "====++++deploy executed successfully++++===="
            }
            failure{
                echo "====++++deploy execution failed++++===="
            }
    
        }
    }
}
