def template = '''
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: docker
  name: docker
spec:
  containers:
  - name: docker
    image: hashicorp/docker
    command:
    - sleep
    - "3600"
'''

podTemplate(cloud: 'kubernetes', label: 'docker', yaml: template ) {
    node("docker") {
        container ("docker") {
            stage ("Checkout SCM") {
                git branch: 'main', url: 'https://github.com/iana-rodyakina/jenkins-february-2025.git'
            }
        }
    }
}

