pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/C1-80417/jk.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_HuaCr3SLfaHxRrIB8bkYEuNF00M | /usr/bin/docker login -u amitr999 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t amitr999/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push amitr999/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 amitr999/mywebsite'
            }
        }
    }
}
