node ('beaware-jenkins-slave') {

 stage('Download Latest') {
        git(url: 'https://github.com/beaware-project/k8s.git', branch: 'master')
   }
    
 stage ('Deploy') {
        sh 'kubectl apply -f combined-ingress-prod-rules.yaml -n prod --validate=false'
   }

}
