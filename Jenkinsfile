// The node label

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
    }
    // Abort here if a newer build has already passed this milestone.
    // Means we don't deploy a superseded build.
    milestone 2

  }
 
    
