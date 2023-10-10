@Library('SharedLibrary1@main')_
import groovy.json.JsonSlurper

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

/*def template_vars = [
    'build_label': 'datascience',
    'node_version' :'fermium',
    'image_dependencies' : [image_dependencies]
]*/

def jsonSlurper = new JsonSlurper()
def template_vars = jsonSlurper.parse(new File('pipelineconf.json'))


def pod1 = renderTemplate(pod, template_vars)
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
