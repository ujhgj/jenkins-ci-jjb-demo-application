pipeline {
    triggers {
        pollSCM('') // Enabling being build on Push
    }
    parameters {
        booleanParam(name: 'LINUX', defaultValue: true, description: '')
        booleanParam(name: 'WINDOWS', defaultValue: true, description: '')
    }

    agent any
    stages {
        stage('Parallel Stage') {
            parallel {
                if (params.LINUX) {
                    stage('Linux') {
                        agent { node "linux-slave" }
                        steps {
                            sh "./node-info.sh | tee linux-node-info.txt"
                            archiveArtifacts artifacts: 'linux-node-info.txt', onlyIfSuccessful: true
                        }
                    }
                }
                if (param.WINDOWS) {
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
}
