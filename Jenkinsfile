pipeline{
    agent any
    environments{
        CREDENTIALS_ID = "terraform-service-account"
    }
    stages{
        stage("launch GCP instance"){
            steps{
                withCredentials([file(credentialsId:env.CREDENTIALS_ID, variable: 'GC_KEY')]){
                    sh """
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
