pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning the code..'
	git 'https://github.com/PareshSwain/SeleniumTestNew.git'
            }
        }
        stage('Clean') {
            steps {
                echo 'Clean..'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true clean"
        	}

            }
        }
        stage('Compile') {
            steps {
                echo 'Compiling....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true compile"
        	}
		}
		}

	

	stage('Package') {
            steps {
                echo 'Packaging....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true package"
        	}
		}
		}

stage('SeleniumTest') {
            steps {
                echo 'FindBugs....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	step([$class: 'Publisher', reportFilenamePattern: '**/testng-results.xml'])
        	}
		}
		}


  
    }
}


