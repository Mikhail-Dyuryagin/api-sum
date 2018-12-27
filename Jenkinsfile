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
        sh 'md5deep -r usr > DEBIAN/md5sums'
        sh 'fakeroot dpkg-deb --build package'
        sh 'mv package.deb api-sum_1.0-1_all.deb'
      }
    }

  }
}

