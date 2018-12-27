pipeline {
  agent any


  stages {
    stage('Build') {
      steps {
        sh 'go build -o APP/usr/bin/api-sum main.go'
      }
    }
    stage('BuildPackage') {
      steps { 
	sh '''       
        find . -type f ! -regex 'md5sum.sh' ! -regex '.*.hg.*' ! -regex '.*?debian-binary.*' ! -regex '.*?DEBIAN.*' -printf '%P ' | xargs md5sum > DEBIAN
        '''
        sh 'fakeroot dpkg-deb --build package'
        sh 'mv package.deb api-sum_1.0-1_all.deb'
      }
    }

  }
}

