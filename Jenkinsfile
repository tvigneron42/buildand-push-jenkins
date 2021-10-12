def pipelineContext = [:]
node {

   def registryProjet='localhost'
   def IMAGE="${registryProjet}:version-${env.BUILD_ID}"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 80:80") { c ->
            sh 'curl localhost'
          }
    }

    stage('Push') {
          docker.withRegistry('https://localhost', 'registry_id') {
              img.push 'latest'
              img.push()
          }
    }

}

