pipeline {
    agent any 
    environment {
        registryURI = "https://registry.hub.docker.com/"
        registry = "prakuldip/kuldip_sample_nginx_jenkinsfile"
        registryCredential = "dockerhub_cred"
    }
stages {
        stage('building docker image') {
            environment {
            iamge_tag = "${env.registryURI}" + ":" + "$GIT_COMMIT"
            }
            steps{
                script {
                def kul_app_image = docker.build(iamge_tag)
                }
            }
        }
        }
        stage('pushing docker image') {
            environment {
            registry_endpoint = "${env.registryURI}" + "${env.registry}"
            }
            steps{
                script {
                    docker.withRegistry(registry_endpoint,registryCredential){
                        kul_app_image.push()
                    }
                }   
            }
        }   
        } 

    }
}