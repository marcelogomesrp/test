pipeline {
    agent any

    triggers {
        cron('H/5 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build logic here'
            }
        }
    }

    when {
        expression {
            // Verifica se a alteração foi uma tag
            changeset ".*refs/tags/.*"
        }
    }
}
