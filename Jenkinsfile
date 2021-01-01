pipeline
 {
  agent any

  stages
   {
    stage('Clean')
     {
      steps
       {
        script
         {
          if (isUnix()) 
           {
            sh 'mvn --batch-mode clean'
           }
          else
           {
            bat 'mvn --batch-mode clean'
           }
         }
       }
     }

    stage('Build')
     {
      steps
       {
        script
         {
          if (isUnix()) 
           {
            sh 'mvn --batch-mode compile'
           }
          else
           {
            bat 'mvn --batch-mode compile'
           }
         }
       }
     }

    stage('UnitTests')
     {
      steps
       {
        script
         {
          if (isUnix()) 
           {
            sh 'mvn --batch-mode resources:testResources compiler:testCompile surefire:test'
           }
          else
           {
            bat 'mvn --batch-mode resources:testResources compiler:testCompile surefire:test'
           }
         }
       }
     }

    stage('Sanity check')
     {
      steps
       {
        script
         {
          if (isUnix()) 
           {
            sh 'mvn --batch-mode checkstyle:checkstyle pmd:pmd pmd:cpd com.github.spotbugs:spotbugs-maven-plugin:spotbugs'
           }
          else
           {
            bat 'mvn --batch-mode checkstyle:checkstyle pmd:pmd pmd:cpd com.github.spotbugs:spotbugs-maven-plugin:spotbugs'
           }
         }
       }
     }

    stage('Packaging')
     {
      steps
       {
        script
         {
          if (isUnix()) 
           {
            sh 'mvn --batch-mode jar:jar'
           }
          else
           {
            bat 'mvn --batch-mode jar:jar'
           }
         }
       }
     }

    stage('install local')
     {
      steps
       {
        script
         {
          if (isUnix()) 
           {
            sh 'mvn --batch-mode jar:jar source:jar install:install'
           }
          else
           {
            bat 'mvn --batch-mode jar:jar source:jar install:install' // maven-jar-plugin falseCreation default is false, so no doubled jar construction here, but required for maven-install-plugin internal data
           }
         }
       }
     }

    stage('Documentation')
     {
      steps
       {
        script
         {
          if (isUnix()) 
           {
            sh 'mvn --batch-mode site'
           }
          else
           {
            echo " Documentation is successfully done.."
           }
         }
       }
     }

    stage('Deploy test')
     {
      steps
       {      
        script
         {
          if (isUnix()) 
           {
            // todo
           }
          else
           {
            echo " Deploying is successfully done.."
           }
         }
       }
     }

    stage('Integration tests')
     {
      steps
       {
        echo "Integration test is successfully done.."
       }
     }
    }
   }
