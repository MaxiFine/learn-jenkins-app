pipeline{
    agent any

    stages{

         stage('Test') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            
            steps {
                sh '''
                    echo 'executing Tests...'
                    test -f build/index.html
                    npm test
                '''
            }
        }
        
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
               sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                    echo 'I am Max'
                '''
            }
        }
    }

    post {
         always {
            junit 'test-results/junt.xml'
         }
    }

       
}