// The node label

  node() {
    
    stage('commit') {
      checkout scm
      sleep 5
      echo "This is the commit stage!"
    }

    // Abort here if a newer build has already passed this milestone.
    // Means we don't run acceptance tests on a superseded build.
    milestone 1

    stage('acceptance'){
      sleep 5
    }

    stage('docker'){
      echo "my Docker repo is ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world:latest"
     sleep 5
      sh 'docker pull hello-world'
      sh 'docker tag hello-world:latest ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world:latest'
      sh 'docker push ec2-34-251-104-14.eu-west-1.compute.amazonaws.com:5000/hello-world:latest'
      
      
      sh 'export AWS_ACCESS_KEY_ID=AKIA42SXKE4JVO2UB6MS'
      sh 'export AWS_SECRET_ACCESS_KEY=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'
      sh 'export AWS_REGION=eu-west-1'
      
      sh 'aws configure set aws_access_key_id AKIA42SXKE4JVO2UB6MS'
      sh 'aws configure set aws_secret_access_key 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'
      sh 'aws configure set default.region eu-west-1'
      sh 'aws configure set default.output json'

      sh 'aws ecr get-login --no-include-email --region eu-west-1'
      sh 'docker tag hello-world:latest 881725155091.dkr.ecr.eu-west-1.amazonaws.com/docker/iata_demo:latest'
      sh 'docker push 881725155091.dkr.ecr.eu-west-1.amazonaws.com/docker/iata_demo:latest'
    }
    // Abort here if a newer build has already passed this milestone.
    // Means we don't deploy a superseded build.
    milestone 2


  }   
