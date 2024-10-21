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
                    test -f build/index.html
                    npm test
                    echo 'test successful'
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


       
}