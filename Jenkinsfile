pipeline{

     triggers {

    githubPush()

  }

agent any

stages('CI CD Pipeline'){

  stage('Code Checkout'){

    steps{

        script{

            git credentialsId: 'GithubCreds', url: 'https://github.com/SheethalBangera/MavenBuild.git'

            }

        }

    }

 

  stage('Build'){

    steps{

        script{

            sh "mvn clean install -Dmaven.test.skip=true"

        }

    }  

  }

  stage('Test'){

    steps{

        script{

            sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"

        }

    }  

  }

  stage('Notification'){

    steps{

        script{

           emailext body: 'Build successful', subject: 'Assignment', to: 'fragstl7@gmail.com'

        }

    }  

  }

}

}
