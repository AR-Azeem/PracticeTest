pipeline {
    agent any
    stages {
        stage ('Clone sources') {
            steps {
               dir('Clone_Source_Code') {
            	    git url: 'https://github.com/AR-Azeem/SourceCode.git', branch: 'Master'
            	}
            }
       	} 
        stage ('compiling Source File'){
            steps{
                bat '''
                    cd Clone_Source_Code
                    IF EXIST TestCaseFailed.txt (
                        del /f TestCaseFailed.txt
                    )
                    javac hello.java 

                 '''

            }
        }
        stage ('Run Source File'){
            steps{
                bat 'cd "Clone_Source_Code" && java A '
            }
        }
         stage ('Error'){
            steps{
               script{ 
                    def script = '''
                    set st=False 
                    cd Clone_Source_Code
                    IF EXIST TestCaseFailed.txt (
                        set st=True
                    )
                    echo %st%
                    '''
                    def status = bat(script: script, returnStdout: true)
                    echo $status
                    if($status){
                        error("failes")
                        echo "good job...."
                    }
                 }
            }
        }

    }
}       