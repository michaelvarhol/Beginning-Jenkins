node {
    printMessage("Pipeline Start")

    stage("Fetch Source Code") {
        git "https://github.com/michaelvarhol/Beginning-Jenkins"
    }

    dir('Lesson5/ActivityA') {
        stage("Install Requirements") {
            sh 'apk update; apk add make python py-pip py3-virtualenv'
            sh 'make install'
            
        }

        stage("Run Tests") {
            sh 'make jenkins_test'
        }

        stage("Deploy") {
            if (env.BRANCH_NAME == "master") {
                printMessage("deploying master branch")
            } else {
                printMessage("no deployment specified for this branch")
            }
        }
    }

    printMessage("Pipeline End")
}

def printMessage(message) {
    echo "${message}"
}
