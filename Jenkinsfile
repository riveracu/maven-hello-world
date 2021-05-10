"pipeline"{
   "agent any
tools"{
      "Maven 3.6.3""and add it to the path.
maven""Maven 3.6.3"
   }"stages"{
      "stage(""Build"")"{
         "steps"{
            "https://github.com/riveracu/maven-hello-world.git",
            "use
bat""mvn -Dmaven.test.failure.ignore=true clean package"
         }"post"{
            ,
            "even if some of the test
// failed",
            "record the test results and archive the jar file.
success"{
               "junit""**/target/surefire-reports/TEST-*.xml""archiveArtifacts""target/*.jar"
            }
         }
      }"stage(""Code Analysis"")"{
         "steps"{
            "withSonarQubeEnv(""SonaQube 8.5 Local"")"{
               "bat""mvn clean package sonar:sonar"
            }
         }
      }
   }
}
