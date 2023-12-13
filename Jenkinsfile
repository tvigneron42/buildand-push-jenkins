node {

   def registryProjet='tibo-app/'
   def IMAGE="${registryProjet}app:1.0"

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
       docker.withRegistry('https://registry.ludovic.io/' , 'tibo_id') {
              img.push 'latest'
              img.push()
          }
    }

}

