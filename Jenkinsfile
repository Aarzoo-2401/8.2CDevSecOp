pipeline {
agent any
stages {
stage('Checkout') {
steps {
git branch: 'main', credentialsId: '31fb5659-eb4b-40f4-a27d-34d984ebc575', url: 'https://github.com/Aarzoo-2401/8.2CDevSecOp.git'
}
}
stage('Install Dependencies') {
steps {
bat 'npm install'
}
}
stage('Run Tests') {
    steps {
        script {
            def testStatus = bat(script: 'npm test', returnStatus: true)
            echo "Test exit code: ${testStatus}"
            if (testStatus != 0) {
                error "Tests failed with exit code ${testStatus}"
            }
        }
    }
}

stage('Generate Coverage Report') {
steps {
// Ensure coverage report exists
bat 'npm run coverage || true'
}
}
stage('NPM Audit (Security Scan)') {
steps {
bat 'npm audit || true' // This will show known CVEs in the output
}
}
}
}
