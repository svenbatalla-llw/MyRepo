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
        bat "2dotnet restore src/HelloWorld/HelloWorld.csproj"
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
      steps
      {
        echo "[Step] Deploying..."
      }
    }
  }
}
