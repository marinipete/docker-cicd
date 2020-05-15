node {
    def app

    stage('Clone reposity'){
        checkout scm
    }

    stage('Build image'){
        app = docker.build('pemarini/example-app')
    }

    stage('Test'){
        app.inside {
            sh 'npm test'
        }
    }

    stage('Push image'){
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials'){
            app.push('latest')
        }
    }
}