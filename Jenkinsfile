pipeline {
  agent any
  stages {
    stage('Prepare') {
      steps {
        cleanWs(deleteDirs: true)
      }
    }

    stage('Pull') {
      steps {
        ws(dir: 'HomePageForNas-frontend') {
          git(url: 'https://github.com/Amosys/HomePageForNas-frontend.git', branch: 'master', changelog: true)
        }

        ws(dir: 'JenkinsJobForNas') {
          git(url: 'https://github.com/Amosys/JenkinsJobForNas.git', branch: 'main', changelog: true)
        }

      }
    }

    stage('Build') {
      steps {
        sh '''cp ./JenkinsJobForNas/HomePageForNas.sh ./HomePageForNas-frontend
cd ./HomePageForNas-frontend
chmod +x ./JenkinsJobForNas/HomePageForNas.sh
./HomePageForNas.sh
cd ..

'''
      }
    }

  }
}