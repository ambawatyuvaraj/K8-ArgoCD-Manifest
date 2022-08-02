node(label: 'updatemanifest'){
    stage(name: 'clone repo'){
        checkout scm
        }
    stage(name: 'Update GIT'){
        script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh """
                          git config user.email raj@cloudwithraj.com"
                          git config user.name RajSaha"
                          cat deployment.yaml"
                          sed -i 's+ambawatyuvaraj/argocd.*+ambawatyuvaraj/argocd:${DOCKERTAG}+g' deployment.yaml"
                          cat deployment.yaml"
                          git add ."
                          git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                          git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/K8-ArgoCD-Manifest.git HEAD:main """
                  }
    }
  }
}
}