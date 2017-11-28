node {
   stage('Compile') {
       milestone()
       checkout([
           $class: 'GitSCM',
           branches: [[name: '*/master']],
           doGenerateSubmoduleConfigurations: false,
           userRemoteConfigs: [
            [
                credentialsId: '37cc48bd-981d-4263-96be-86b430cefdcd',
                url: 'https://github.com/michaelmeire/devopscourse-jenkinspipeline-michael.git']
            ]
           ]
       )
       sh 'chmod +x ./gradlew'
       sh './gradlew clean build -x check'
   }
   stage('Test') {
       milestone()
       sh './gradlew build'
       archive "build/test-results/**/*"
       junit 'build/test-results/**/*.xml'
   }
}