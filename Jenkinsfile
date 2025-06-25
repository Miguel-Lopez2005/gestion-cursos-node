pipeline {
  agent any

  stages {
    stage('Clonar repositorio') {
      steps {
        git branch: 'main', url: 'https://github.com/Miguel-Lopez2005/gestion-cursos-node.git'
      }
    }

    stage('SBOM - Generar inventario de componentes') {
      steps {
        sh '''
          docker run --rm -v $(pwd):/app anchore/syft dir:/app -o json > sbom.json
        '''
        archiveArtifacts artifacts: 'sbom.json', fingerprint: true
      }
    }
  }
}
