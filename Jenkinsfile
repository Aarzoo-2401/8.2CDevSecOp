pipeline {
agent any
stages {
stage('Checkout') {
steps {
git credentialsId: 'github-token', url: ' https://github.com/Aarzoo-2401/8.2CDevSecOps.git'
}
}
stage('Install Dependencies') {
steps {
bat 'npm install'
}
}
stage('Run Tests') {
steps {
bat 'npm test || true' // Allows pipeline to continue despite test failures
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
