pipeline {
	agent any
	
	environment {
		BuildConfiguration="Debug"
	}

	stages {
		stage('Build') {
			steps {
				sh "dotnet build -c $BuildConfiguration"
			}
		}

		stage('Test') {
			steps {
				sh 'dotnet test -c $BuildConfiguration --no-build'
			}
		}

		
		stage('Pack') {
			steps {
				sh 'dotnet pack TGS.Core.Infrastructures.Helper/TGS.Core.Infrastructures.Helper.csproj -c $BuildConfiguration --no-build --no-restore'
			}
		}
		
		stage('Push Nuget') {   
			steps {
				sh  'dotnet nuget push TGS.Core.Infrastructures.Helper/bin/$BuildConfiguration/*.nupkg --source "raypro" --skip-duplicate'
			}
		}
	}
}