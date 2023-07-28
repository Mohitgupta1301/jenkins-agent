pipeline {
    agent any

    stages {
        stage('Create Dynamic Agent') {
            steps {
                // Create a new agent with a label
                def agent = nodes.add(label: 'jenkins-agent', numExecutors: 1)

                // Set the environment variables for the agent
                env.MY_VARIABLE = 'some value'

                // Save the agent configuration
                nodes.save()
            }
        }

        stage('Build Docker Image') {
            steps {
                // Use the dynamic agent to run the build process
                node('jenkins-agent') {
                    git 'https://github.com/Mohitgupta1301/jenkins-agent.git'
                    sh 'docker build -t jenkinsdockerfile .'
                }
            }
        }
    }
}
