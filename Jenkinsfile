pipeline{
	agent any

	stages {
	    stage('Git-checkout') {
	        steps{
	            echo "Checking out from git repo"
	            // git branch: 'main', url: 'https://github.com/LakhiCharanMahato/Jenkins_Trial.git'
	        }
	    }
		stage('Build'){
			steps{
				echo "Building the project";
				sh 'ls -l';
				sh 'sh Build.sh'
			}
		}

		stage('JUnit'){
			steps{
				echo "Running JUnit tests"	
				sh 'sh Unit.bat'
			}
		}

		stage('Quality-Gate'){
			steps{
				echo "SonarQube Quality running !!"
				sh 'sh Quality.bat'
			}
		}

		stage('Deploy'){
			steps{
				echo "Deploying"
				sh 'sh Deploy.bat'
			}
		}
	}
	
	post{
		always{
			echo 'This will always run'
		}
		success{
			echo 'This will run only if successfull'
		}
		failure{
			echo 'This will run only if failed'
		}
		unstable{	
			echo 'This will run only if run was marked as unstable'
		}
		changed{
			echo 'This will run only if the state of the Pipeline has changed'
			echo 'For example, if pipeline was previously failing but is now successfull'
		}
	}
}