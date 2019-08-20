//TODO: use standard buildComponent() step from the Pipeline library once ready

/* Only keep the 10 most recent builds. */
properties([[$class: 'BuildDiscarderProperty',
                strategy: [$class: 'LogRotator', numToKeepStr: '10']]])


/* These platforms correspond to labels in ci.jenkins.io, see:
 *  https://github.com/jenkins-infra/documentation/blob/master/ci.adoc
 */
node('maven') {
    timestamps {
        stage('Checkout') {
            checkout scm
        }

        stage('Build') {
           runMaven(["clean", "install"])
        }

        stage('Archive') {
            archiveArtifacts artifacts: 'target/**/*.jar,target/**/*.zip'
        }
    }
}

