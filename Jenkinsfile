node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage("delete container"){
        steps{
            echo "====++++executing delete container++++===="
        }
        post{
            always{
                echo "====++++always++++===="
                'sh docker rm -f $(docker ps -a -f name=dockerreact_v1 -q)'
            }
            success{
                echo "====++++delete container executed successfully++++===="
            }
            failure{
                echo "====++++delete container execution failed++++===="
            }
    
        }
    }

    stage('Build image') {
        app = docker.build("dockerreact_v1","-f Dockerfile.dev .")
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
