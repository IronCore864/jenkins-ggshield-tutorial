podTemplate(containers: [
    containerTemplate(name: 'ggshield', image: 'gitguardian/ggshield:latest', command: 'sleep', args: '99d', runAsUser: '1000')
  ]) {

    node(POD_LABEL) {
        stage('Get a project') {
            git url:'https://github.com/IronCore864/k8s-vagrant-kubeadm.git', branch: 'main'
            container('ggshield') {
                stage('Scan a project') {
                    sh 'ggshield scan path --recursive -y .'
                }
            }
        }
    }
}
