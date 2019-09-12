// The node label
export docker_repo=ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world
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
     sleep 10
      docker pull hello-world
      docker tag hello-world ${docker_repo}
      docker push ${docker_repo}
    }
    // Abort here if a newer build has already passed this milestone.
    // Means we don't deploy a superseded build.
    milestone 2

  }
 
    
