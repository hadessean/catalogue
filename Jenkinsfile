@Library('jenkins-shared-library') _

def configMap = [
    type      : "nodejsEKS",
    component : "catalogue",
    project   : "roboshop"
]

node {

    stage('Pipeline Initialization') {
        echo "Component: ${configMap.component}"
        echo "Project: ${configMap.project}"
        echo "Pipeline Type: ${configMap.type}"
        echo "Branch: ${env.BRANCH_NAME}"
    }

    stage('Pipeline Decision') {

        if (!env.BRANCH_NAME.equalsIgnoreCase('main')) {

            echo "Non-main branch detected"
            pipelineDecission.decidePipeline(configMap)

        } else {

            echo "Main branch detected"
            echo "Proceed with CR or NON-PROD pipeline"
        }
    }
}
