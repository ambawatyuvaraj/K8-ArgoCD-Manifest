node{
    stage(name: 'clone repo'){
        checkout scm
        }
    stage(name: 'Update GIT'){
        script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    
                        sh """
                          git config user.email yuvrajpael008@outlook.com"
                          git config user.name Ambawat Yuvaraj"
                          cat Deployment.yaml"
                          sed -i 's+ambawatyuvaraj/argocd.*+ambawatyuvaraj/argocd:${DOCKERTAG}+g' Deployment.yaml"
                          cat Deployment.yaml"
                          git add ."
                          git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"""
                          withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                            sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/K8-ArgoCD-Manifest.git HEAD:main"
                  }
    }
  }
}
}