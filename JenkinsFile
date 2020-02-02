#!/usr/bin/env groovy
def appName= 'testing'
def major_version = 1.0 


node{ 

stage('cloning repo'){
  checkout scm
}

  stage('Test'){
sh 'mvn clean test'
}

stage('Build'){
echo "Building app with name ${appName}"
sh 'mvn clean install'
}
  
  stage('renaming jar'){
    def build_number =  BUILD_NUMBER
    def appVersion = major_version + build_number
    sh "mv $WORKSPACE/target/jb*.jar $WORKSPACE/target/${appName}.${appVersion}.jar"
    echo "The current application name is ${appName}.${appVersion}.jar"
    sh 'ls -la target/'
  }
  
}
