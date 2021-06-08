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
        stage ('compiling Source File'){
            steps{
                bat """
                    cd 'Clone Source Code'
                    IF EXIST TestCaseFailed.txt (
                        del /f TestCaseFailed.txt
                    )
                    javac hello.java 

                 """

            }
        }
        stage ('Run Source File'){
            steps{
                bat 'cd "Clone Source Code" && java A '
            }
        }
         stage ('Error'){
            steps{
                IF EXIST TestCaseFailed.txt (
                     error("TestCase Failed")
                 )
                
            }
        }

    }
}       