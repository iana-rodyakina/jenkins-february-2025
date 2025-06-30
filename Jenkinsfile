def template = '''
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: docker
spec:
  volumes:
  - name: docker-sock
    hostPath:
      path: /var/run/docker.sock
  containers:
  - name: docker
    image: docker
    command:
    - sleep
    - "3600"
    volumeMounts:
    - name: docker-sock
      mountPath: /var/run/docker.sock
'''
   

podTemplate(cloud: 'kubernetes', label: 'docker', yaml: template ) {
    node("docker") {
        container ("docker") {
        stage ("Checkout SCM") {
                git branch: 'main', url: 'https://github.com/iana-rodyakina/jenkins-february-2025.git'
            }
        stage('Docker Build') {
           sh "docker build -t iana-rodyakina/myapache:1.0.0 ."
}
        }
        }
    }
}

