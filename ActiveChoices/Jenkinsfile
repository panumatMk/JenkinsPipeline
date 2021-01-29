String movieNames = 
'''if(MovieType.equals("Action")){
    return ["Black Panther","Avengers: Endgame","John Wick"]
}else if(MovieType.equals("Comedy")){
    return ["Jumanji","Despicable Me"]
}else if(MovieType.equals("Drama")){
    return ["Me Before You"]
}'''

String  movieTypes = 
'return [\'Action:selected\',\'Comedy\',\'Drama\']'

properties(
    [
        parameters(
            [
                [$class: 'ChoiceParameter',
                choiceType: 'PT_RADIO',
                description: '',
                filterLength: 1,
                filterable: false,
                name: 'MovieType',
                randomName: 'choice-parameter-11512403937572165',
                script: 
                    [
                        $class: 'GroovyScript', 
                        fallbackScript: [
                            classpath: [], 
                            sandbox: false, 
                            script: 'return [\'error\']'
                        ], 
                        script: [
                            classpath: [],
                            sandbox: false, 
                            script: movieTypes
                        ]
                    
                    ]
                ], 
                [$class: 'CascadeChoiceParameter',
                choiceType: 'PT_RADIO',
                description: '',
                filterLength: 1,
                filterable: false,
                name: 'MovieName',
                randomName: 'choice-parameter-11512403946950068',
                referencedParameters: 'MovieType',
                script: 
                    [
                        $class: 'GroovyScript',
                        fallbackScript:[
                            classpath: [], 
                            sandbox: false, 
                            script: 'return [\'error\']'
                        ], 
                        script: 
                            [
                                classpath: [], 
                                sandbox: false, 
                                script: movieNames
                            ]
                    ]
                ]
            ]
        )
    ]
)

pipeline {
    agent none
    stages {
        stage('prepare') {
            agent { label 'master' }
            steps {
                script {
                    
                    echo "Movie type is " + params.MovieType+"."

                    echo "Movie name is "params.MovieName+"."
                }
            }
        }
    }
}