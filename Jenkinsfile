pipeline{
    agent { label 'build' }
    stages{
        stage('file'){
            steps{
                sh 'pwd'
                dir('/root/golden-image/') {
                sh 'ls -l'
                }
            }
        }
        stage('init'){
            steps{
                dir('/root/golden-image/') {
                sh 'packer init .'
                }
            }
        }
        stage('fmt'){
            steps{
                dir('/root/golden-image/') {
                sh 'packer fmt .'
                }
            }
        }
        stage('validate'){
            steps{
                dir('/root/golden-image/') {
                sh 'packer validate .'
                }
            }
        }
        stage('build'){
            steps{
                dir('/root/golden-image/') {
                sh 'packer build .'
                }
            }
        }
        stage('filez'){
            steps{
                dir('/root/infra/') {
                sh 'ls -l'
                }
            }
        }
        stage('terra-init'){
            steps{
                dir('/root/infra/') {
                sh 'terraform init'
                }
            }
        }
        stage('terra-plan'){
            steps{
                dir('/root/infra/') {
                sh 'terraform plan'
                }
            }
        }
        stage('terra-apply'){
            steps{
                dir('/root/infra/') {
                sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
