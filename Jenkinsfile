pipeline {
    agent {
        kubernetes {
        //cloud 'kubernetes'
            containerTemplate {
            name 'jupyter-helm'
            image 'jshimko/kube-tools-aws:latest'
            ttyEnabled true
            command 'cat'
            }
        }
    }

    environment {
        AWS_ACCESS_KEY_ID =  credentials('aws_access_key_id')
        AWS_SECRET_ACCESS_KEY = credentials('aws_secret_access_key')
        AWS_DEFAULT_REGION = 'eu-north-1'
    }

        stages {
            stage('Helm init'){
                steps {
                    // withCredentials([file(credentialsId: 'kubeconfig', variable: 'config')]) {
                    //     sh "export KUBECONFIG=\${config}"
                        //sh "kubectl create ns jupyter"
                        //sh "kubectl config set-context arn:aws:eks:eu-north-1:586301231170:cluster/eks_cluster_devops --namespace=jupyter"  
                        //Deploy with Helm  echo "Deploying"  sh "helm upgrade --install road-dashboard -f values.${ENV}.yaml --set tag=$TAG --namespace ${namespace}"
                        sh "aws eks update-kubeconfig --name eks_cluster_devops"
                        // sh 'wget https://get.helm.sh/helm-v3.6.1-linux-amd64.tar.gz'
                        // sh 'ls -a'
                        // sh 'tar -xvzf helm-v3.6.1-linux-amd64.tar.gz'
                        // sh 'sudo cp linux-amd64/helm /usr/bin'
                        sh 'helm version'
                        sh 'ls'
                        //sh "kubectl create ns jupyter"
                        sh "helm repo add bitnami https://charts.bitnami.com/bitnami/jupyterhub"
                        sh "helm repo update"
                        sh "helm install jhub-datascience bitnami/jupyterhub -f jupyter-bitnami-values.yaml -n jupyter"
                    // }               

                }
            }   
        }         
 
}     