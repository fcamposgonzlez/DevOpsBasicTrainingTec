//tell jenkins this is a pipeline
pipeline {
 
    //Determine in which node will the pipeline be executed
    agent any
	
	stages {
		stage('before') {
            steps {
                sh 'python3 --version'
                sh 'pip3 install -r requirements.txt'
            }
		}
		//add build step on tox
        stage('build') {
            steps {
                sh 'python3 -m tox -e build'
            }
        }
		stage('test') {
            when{
                //only execute tests is test parameter is true
                expression { params.test == true }
            }
            steps {
                sh 'python3 -m tox -e test'
            }
        }
    }
}