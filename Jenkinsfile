properties([
    parameters([
        [$class: 'ChoiceParameter', 
            choiceType: 'PT_SINGLE_SELECT', 
            description: 'Select the Environment Name from the Dropdown List', 
            filterLength: 1, 
            filterable: false, 
            name: 'Environment', 
          //  randomName: 'choice-parameter-5631314439613978', 
            script: [
                $class: 'GroovyScript', 
                fallbackScript: [
                    classpath: [], 
                    sandbox: true, 
                    script: 
                        'return[\'Could not get Env\']'
                ], 
                script: [
                    classpath: [], 
                    sandbox: true, 
                    script: 
                        'return["Dev","QA","Stage","Prod"]'
                ]
            ]
        ],
       [$class: 'CascadeChoiceParameter', 
            choiceType: 'PT_SINGLE_SELECT', 
            description: 'Select the Server from the Dropdown List', 
            filterLength: 1, 
            filterable: false, 
            name: 'Server', 
          //  randomName: 'choice-parameter-5631314456178619', 
            referencedParameters: 'Environment', 
            script: [
                $class: 'GroovyScript', 
                fallbackScript: [
                    classpath: [], 
                    sandbox: false, 
                    script: 
                        'return[\'Could not get Environment from Env Param\']'
                ], 
                script: [
                   classpath: [], 
                    sandbox: false, 
                    script: 
                        ''' if (Env.equals("Dev")){
                                return["devaaa001","devaaa002","devbbb001","devbbb002","devccc001","devccc002"]
                            }
                            else if(Env.equals("QA")){
                                return["qaaaa001","qabbb002","qaccc003"]
                            }
                            else if(Env.equals("Stage")){
                                return["staaa001","stbbb002","stccc003"]
                            }
                            else if(Env.equals("Prod")){
                                return["praaa001","prbbb002","prccc003"]
                            }
                        '''
                ]
            ]
        ]
    ])
])

import groovy.json.JsonSlurper

pipeline {
  /**environment {
         vari = ""
  } **/
  agent any
  stages {
      stage ("Example") {
        steps {
         script{
          echo 'Hello'
          echo "Environment is ${params.Environment}"
          echo "Server selected is ${params.Server}"
          if (params.Server.equals("Could not get Environment from Environment Param")) {
              echo "Must be the first build after Pipeline deployment.  Aborting the build"
              currentBuild.result = 'ABORTED'
              return
          }
          echo "Crossed param validation"
        } }
      }
  }
}
