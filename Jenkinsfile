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
         withCredentials([usernamePassword(credentialsId: 'docker-creds', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {

        stadge ("Docker Login") {
            sh "docker Login -u ${DOCER_USER} -p ${DOKER_PASS}"
        }
        stage("Docker Build") {
           sh "docker build -t ${DOCER_USER}/myapache:1.0.0 ."
        }
        stage ("Docker Push") {
            sh "docker push ${DOCER_USER}/myapache:1.0.0 ."
        }
        }
    }
    }
}


