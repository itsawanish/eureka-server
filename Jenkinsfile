pipeline {
agent any 
stages { 
stage('Checkout Code') { 
steps { 
git branch: 'main', 
url: 'https://github.com/itsawanish/eureka-server.git' 
} 
} 
stage('Build Application') { 
steps {  
bat 'mvn clean package -DskipTests' 
} 
} 
stage('Build Docker Image') { 
steps { 
bat 'docker build -t eureka-server:1.2 .' 
} 
} 
stage('Stop Old Container') { 
steps { 
bat 'docker stop eureka-container || exit 0' 
bat 'docker rm eureka-container || exit 0' 
} 
} 
stage('Run Docker Container') { 
steps { 
bat 'docker run -d -p 8761:8761 --name eureka-container eureka-server:1.2' 
} 
} 
} 
}
