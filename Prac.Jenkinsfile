pipeline {
    agent any
    stages {
        stage ('Clone sources') {
            steps {
               dir('Clone Source Code') {
            	    git url: 'https://github.com/AR-Azeem/SourceCode.git', branch: 'Master'
            	}
            }
       	} 

    }
}       