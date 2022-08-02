node{
    stage(name: 'clone repo'){
        checkout scm
        }
    stage(name: 'Update GIT'){
        script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        
                        sh "git config user.email yuvrajpatel008@outlook.com"
                        sh "git config user.name Ambawat Yuvaraj"
                       
                        sh "cat deployment.yaml"
                        sh "sed -i 's+raj80dockerid/test.*+raj80dockerid/test:${DOCKERTAG}+g' Deployment.yaml"
                        sh "cat Deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job updatemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/K8-ArgoCD-Manifest.git HEAD:main"
                    }
                }
}
}
}