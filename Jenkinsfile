properties([
   parameters([
        [$class: 'ChoiceParameter', 
            choiceType: 'PT_SINGLE_SELECT',
            description: 'Select the environment to which deployment is done.', 
            filterLength: 1, 
            filterable: false, 
            name: 'ENVIRONMENT',
            script: [
                $class: 'GroovyScript', 
                fallbackScript: [
                    classpath: [], 
                    sandbox: true, 
                    script: 'return["Error"]'
                ], 
                script: [
                    classpath: [], 
                    sandbox: true, 
                    script: 'return["","HIT1", "HIT2","SIT2","SIT1","UAT2","DT"]'
                ]
            ]
        ]
])
])   
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               echo 'Stage 1 done'
            }
        }
        stage('Test') {
            steps {
                echo 'Stage 2 done;'
            }
        }    
    }
    
}
