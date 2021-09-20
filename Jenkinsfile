pipeline {
    agent any
    stages {
        stage('Parallel Stage') {
            parallel {
                stage('Linux') {
                    agent { node "linux-slave" }
                    steps {
                        sh "./node-info.sh | tee linux-node-info.txt"
                        archiveArtifacts artifacts: 'linux-node-info.txt', onlyIfSuccessful: true
                    }
                }
                stage('Windows') {
                    agent { node "windows-slave" }
                    steps {
                        bat "powershell.exe .\\node-info.ps1 > windows-node-info.txt"
                        bat "type windows-node-info.txt"
                        archiveArtifacts artifacts: 'windows-node-info.txt', onlyIfSuccessful: true
                    }
                }
            }
        }
    }
}
