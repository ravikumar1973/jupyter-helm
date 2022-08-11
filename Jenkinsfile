pipeline {
    agent {
        kubernetes {
        //cloud 'kubernetes'
            containerTemplate {
            name 'jupyter-helm'
            image 'ibmcom/ibm-cloud-developer-tools-amd64'
            ttyEnabled true
            command 'cat'
            }
        }
    }

        stages {
            stage('Helm init'){
                steps {
                    withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
                        //sh "kubectl create ns jupyter"
                        //sh "kubectl config set-context arn:aws:eks:eu-north-1:586301231170:cluster/eks_cluster_devops --namespace=jupyter"  
                        //Deploy with Helm  echo "Deploying"  sh "helm upgrade --install road-dashboard -f values.${ENV}.yaml --set tag=$TAG --namespace ${namespace}"
                        sh "sleep 300"
                        sh "kubectl get no"
                    }               

                }
            }   
        }         
 
}     