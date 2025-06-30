templaste =  '''
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: docker
  name: docker
spec:
  containers:
  - command:
    - sleep
    - "3600"
    image: hashicorp/docker
    name: docker
'''

podTemplate(cloud: 'kubernetes', label: 'docker', yaml: temlate ) {
node ("docker") {
    container ("docker") {
    stage ("Checkout SCM") {
        git branch: 'main', url: 'https://github.com/iana-rodyakina/jenkins-february-2025.git'
    }
    }
}
}

