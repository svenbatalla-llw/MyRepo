pipeline
{
  agent any
  
  stages
  {
    stage("build")
    {
      steps
      {
        echo "[Step] Building..."
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
        echo "[Step] Testing..."
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
        echo "[Step] Deploying..."
        bat "xcopy .\\src\\HelloWorld\\bin\\Debug\\netcoreapp3.1 c:\\demo\\HelloWorld /SIY"
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
