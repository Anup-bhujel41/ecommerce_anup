pipeline {
  
    agent any
   
    stages {
        stage('build') {
            steps {
              sh 'FROM python:3'
              sh 'RUN pip install django==3.2'
              sh 'RUN python3 manage.py makemigrations'
              sh 'RUN python3 manage.py migrate'
            }
        }

       stage('deploy') {
            steps {
                sh 'CMD python manage.py runserver 0.0.0.0:8000'
            }
        }

    }
}
