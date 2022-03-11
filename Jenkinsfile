// v1
// pipeline {
//     agent any
//     //tools {
//     //    maven 'localMaven'
//     //}
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'mvn clean package'
//             }
//             post {
//                 success {
//                     echo 'Now Archiving...'
//                     archiveArtifacts artifacts: '**/target/*.war'
//                 }
//             }
//         }
//     }
// }
// v2
// pipeline {
//     agent any
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'mvn clean package'
//             }
//             post {
//                 success {
//                     echo 'Now Archiving...'
//                     archiveArtifacts artifacts: '**/target/*.war'
//                 }
//             }
//         }
//         stage('Deploy to Staging') {
//             steps {
//                 build job: 'Deploy-to-staging'
//             }
//         }
//     }
// }
// v3
// pipeline {
//     agent any
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'mvn clean package'
//             }
//             post {
//                 success {
//                     echo 'Now Archiving...'
//                     archiveArtifacts artifacts: '**/target/*.war'
//                 }
//             }
//         }
//         stage('Deploy to Staging') {
//             steps {
//                 build job: 'Deploy-to-staging'
//             }
//         }

//         stage('Deploy to Production') {
//             steps{
//                 timeout(time:5, unit:'DAYS') {
//                     input message:'Approve PRODUCTION Deployment?'
//                 }

//                 build job: 'Deploy-to-Prod'
//             }
//             post {
//                 success {
//                     echo 'Code deployed to Production.'
//                 }

//                 failure {
//                     echo ' Deployment failed.'
//                 }
//             }
//         }
//     }
// }

//aws
// pipeline {
//     agent any

//     parameters {
//         string(name: 'tomcat_dev', defaultValue: '35.172.183.153', description: 'Staging Server')
//         string(name: 'tomcat_prod', defaultValue: '34.224.68.127', description: 'Production Server')
//     }

//     triggers {
//         pollSCM('* * * * *')
//     }

//     stages {
//         stage('Build') {
//             steps {
//                 sh 'mvn clean package'
//             }
//             post {
//                 success {
//                     echo 'Now Archiving...'
//                     archiveArtifacts artifacts: '**/target/*.war'
//                 }
//             }
//         }

//         stage('Deployments') {
//             parallel {
//                 stage('Deploy to Staging') {
//                     steps {
//                         sh "scp -i /tmp/tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_dev}:/var/apache-tomcat-9.0.59/webapps"
//                     }
//                 }

//                 stage('Deploy to Production') {
//                     steps {
//                         sh "scp -i /tmp/tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_prod}:/var/apache-tomcat-9.0.59/webapps"
//                     }
//                 }
//             }
//         }
//     }
// }

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
    }
}