node ('beaware-jenkins-slave') {


    stage ('Deploy') {
        sh 'kubectl apply -f combined-ingress-prod-rules.yaml -n prod --validate=false'
    }

}
