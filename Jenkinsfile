pipeline{
    agent any
    environment{
        CREDENTIALS_ID = "terraform-service-account"
    }
    stages{
        stage("launch GCP instance"){
            steps{
                withCredentials([file(credentialsId:env.CREDENTIALS_ID, variable: 'GC_KEY')]){
                    sh """
                        export GOOGLE_APPLICATION_CREDENTIALS=$GC_KEY
                        cd terraform_scripts/compute_instance
                        terraform init
                        terraform plan
                        terraform apply -auto-approve
                        """
                }
            }
        }
    }
}
