pipeline
{
  agent any
  
  stages
  {
    stage("build")
    {
      steps
      {
        echo "[Step (build: ${env.BUILD_NUMBER})] Building..."
        bat "dotnet restore src/HelloWorld/HelloWorld.csproj"
        bat "dotnet clean src/HelloWorld/HelloWorld.csproj"
        bat "dotnet build src/HelloWorld/HelloWorld.csproj"
        archiveArtifacts artifacts: "src/HelloWorld/bin/**"
      }
    }

    stage("test")
    {
      steps
      {
        echo "[Step (build: ${env.BUILD_NUMBER})] Testing..."
      }
    }

    stage("deploy")
    {
      when
      {
        expression
        {
          currentBuild.result == null || currentBuild.result == "SUCCESS"
        }
      }
      
      steps
      {
        echo "[Step (build: ${env.BUILD_NUMBER})] Deploying..."
        bat "xcopy .\\src\\HelloWorld\\bin\\Debug\\netcoreapp3.1 c:\\demo\\HelloWorld_${env.BUILD_NUMBER} /SIY"
      }
    }
  }
  
  post
  {
    failure
    {
      echo "The build has failed! Call someone!"
    }
  }
}
