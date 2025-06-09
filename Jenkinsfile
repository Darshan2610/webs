pipeline{
    agent any
    tools{
        maven 'maven'
        jdk 'java-11'
    }
    
    stages{
        stage('checkout'){
        steps{
        git branch:'master',url:'https://github.com/Darshan2610/webs.git'
        }
        }
    
    
    stage('build'){
        steps{sh 'mvn clean package'}
        
    }
    
    stage('archive'){
        steps{
            archiveArtifacts artifacts: 'target/*.war' , fingerprint:true
        }
    }
    
    stage('deploy'){
        steps{
            sh 'mvn clean package'
            ansiblePlaybook playbook:'ansible/deploy.yml' , inventory:'ansible.hosts.ini'
        }
    }
    
    }
    

}
