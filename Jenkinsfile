@Library('SharedLibrary1@main')_

//service name is extrapolated from repository name
def svcName = currentBuild.rawBuild.project.parent.displayName

//get pod template definition
def pod = libraryResource 'com/org/service/k8s-pod-template.yaml'
def image_dependencies =
'''
    - name: fermium-alpine
      image: node:fermium-alpine
      imagePullPolicy: IfNotPresent
      command:
        - cat
      tty: true
'''

def application_vars = [
    'pod_template_common': [
        'build_label': 'datascience',
        'node_version' :'fermium',
        'image_dependencies' : [image_dependencies]
    ],
    'pod_template': [
        'container1': [ 
            'type': 'maven',
            'version': '3.3.9'
        ],
        'container2': [
            'type': 'docker',
            'verison': '23.0'
        ]
    ]
]

def podtemplate = renderTemplate(pod, application_vars['pod_template_common'])
def podtemplate = renderTemplate(podtemplate, application_vars['pod_template'])
echo 'Pod Template: ' + pod1 + ';'

//def engine = new groovy.text.SimpleTemplateEngine()
//def template = engine.createTemplate(pod).make(template_vars)

//echo 'Hello Mr.' + template + ';'


/*def sharedLibrary = new com.org.service.testsharedlib()

def compileData = [run: true]
def testData = [run: true]
def artifactData = [run: true]
def intTestData = [run: true]
def deploymentData = [run: true]
def afterDeployData = [run: true]

def buildCommands = [
    compileData: compileData,
    testData: testData,
    artifactData: artifactData,
    intTestData: intTestData,
    deploymentData: deploymentData,
    afterDeployData: afterDeployData
]

// Set slack channel
def slackChannel = "k8s-jenkins"

timestamps {
    commonPipeline(sharedLibrary, svcName, buildCommands, pod, slackChannel)
}
*/
