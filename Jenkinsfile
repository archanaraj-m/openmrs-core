node('OPENMRS')
{
    stage('vcs') { 
        git branch: 'scripted',
            url:'https://github.com/archanaraj-m/openmrs-core.git'
    }
    stage ('build') {
        sh 'export PATH="/usr/lib/jvm/java-1.11.0-openjdk-amd64/bin:$PATH" && mvn package'
    }
    stage('postbuild') {
        archiveArtifacts artifacts: '**/target/*.jar',
                         onlyIfSuccessful: true
        junit testResults: '**/TEST-*.xml'
    }
}