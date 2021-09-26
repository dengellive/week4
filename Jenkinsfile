podTemplate(
    containers: [
        containerTemplate(
            name: 'maven', 
            image: 'maven:3.8.1-jdk-8', 
            command: 'sleep', 
            args: '30d'
        )
  ],
  volumes: [
      persistentVolumeClaim(claimName: 'maven-pv-claim', mountPath: '/home/linuxadmin/week4/data')
      
  ]) {
    node(POD_LABEL) {
        stage('Get a Maven project') {
            git 'github.com/dlambrig/simple-java-maven-app.git'
            container('maven') {
                stage('Build a Maven project') {
                    sh '''
                    echo "maven build"
                    mvn -B -DskipTests clean package
                    '''
                    }
            }
        }
    }
  }
