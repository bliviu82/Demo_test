// The node label

def docker_repo="ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world" 

  node() {
    
    stage('commit') {
      checkout scm
      sleep 10
      
    }

    // Abort here if a newer build has already passed this milestone.
    // Means we don't run acceptance tests on a superseded build.
    milestone 1

    stage('acceptance'){
      sleep 10
    }

    stage('docker'){
      echo "my Docker repo is ${docker_repo}"
     sleep 10
      sh 'docker pull hello-world'
      sh 'docker tag hello-world ${docker_repo}'
      sh 'docker push ${docker_repo}'
    }
    // Abort here if a newer build has already passed this milestone.
    // Means we don't deploy a superseded build.
    milestone 2

  }
 
    
