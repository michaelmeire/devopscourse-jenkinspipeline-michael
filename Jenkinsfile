node {
   stage('Compile') {
       milestone()
       checkout([
           $class: 'GitSCM',
           branches: [[name: '*/master']],
           doGenerateSubmoduleConfigurations: false,
           extensions: [],
           submoduleCfg: [],
           userRemoteConfigs: [
            [
                credentialsId: '37cc48bd-981d-4263-96be-86b430cefdcd',
                url: 'https://github.com/michaelmeire/devopscourse-jenkinspipeline-michael.git']
            ]
           ]
       )
       chmod +x ./gradlew
       sh './gradlew build -x check'
   }
   stage('Test') {
       milestone()
   }
}