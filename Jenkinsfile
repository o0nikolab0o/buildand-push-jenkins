def pipelineContext = [:]
node {

   def registryProjet='burdyburd/'
   def IMAGE="${registryProjet}apache:version-${env.BUILD_ID}"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 8000:80") { c ->
       
          }
    }

    stage('Push') {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub') {
              img.push 'latest'
              img.push()
          }
    }

}

