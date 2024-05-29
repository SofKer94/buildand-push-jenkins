node {

   def registryProjet='jenkins_sofiane/'
   def IMAGE="${registryProjet}app:3.9"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
          }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID") { c ->
       
          }
    }

    stage('Push') {
       docker.withRegistry('https://registry.ludovic.io/' , 'harbor_id') {
              img.push 'latest'
              img.push()
          }
    }
   stage('Compose up') {
       sh 'docker compose up --detach'
    }

}

