// The node label

  node() {
    
    stage('commit') {
      checkout scm
      sleep 10
      echo "This is the commit stage!"
    }

    // Abort here if a newer build has already passed this milestone.
    // Means we don't run acceptance tests on a superseded build.
    milestone 1

    stage('acceptance'){
      sleep 10
    }

    stage('docker'){
      echo "my Docker repo is ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world:latest"
     sleep 10
      sh 'docker pull hello-world'
      sh 'docker tag hello-world:latest ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world:latest'
      sh 'docker push ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world:latest'
      
      eval $(aws ecr get-login --no-include-email | sed 's|https://||')
      docker login -u AWS -p -e none https://881725155091.dkr.ecr.eu-west-1.amazonaws.com
      sh 'docker tag hello-world:latest 881725155091.dkr.ecr.eu-west-1.amazonaws.com/docker/iata_demo/hello-world:latest'
      sh 'docker push 881725155091.dkr.ecr.eu-west-1.amazonaws.com/docker/iata_demo/hello-world:latest'
    }
    // Abort here if a newer build has already passed this milestone.
    // Means we don't deploy a superseded build.
    milestone 2

  }   
