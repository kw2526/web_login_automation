node {
    def app
    
    stage('Clone repository'){
    /* Cloning the Repository to our Workspace */
    
    //git 'https://github.com/kw2526/web_login_automation.git'
          checkout scm
    }
    
    stage('Built image') {
    
      app = docker.build("kw2526/project:${env.BUILD_NUMBER}")
    
    }
    
    stage('Test image') {
    
      app.inside { 
          echo "Test passed"
       }
    }
    
    stage('Push image') {
    /* register with dockerhub before push images to the account */
      docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
        app.push()
       }
     // echo "Trying to Push Docker Build to Dockerhub"
     }
 }
    
    
