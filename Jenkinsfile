node('jdk11-mvn3.8.4') {
    stage('git') {
        git branch: 'master', url: 'https://github.com/bhargavi-vaduguri/python-sample-vscode-flask-tutorial.git'
    }
    stage('build') {
        sh 'python3 -m pip help install'
        sh 'pip install -r requirements.txt'
    } 
    stage('test') {
         sh 'pip install pytest pytest-azurepipelines' 
         sh 'pip install pytest-cov'
         sh '/home/devops/.local/bin/pytest --doctest-modules --junitxml=junit/test-results.xml --cov=. --cov-report=xml'
    } 
    stage('publish') {
        junit testResults: '**/test-*.xml'
    }
}