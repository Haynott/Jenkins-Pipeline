pipeline {
    agent any

    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo "Building the code using setuptools."
                echo "Setuptools is a Python package that simplifies the process of packaging and distributing Python projects."
                echo "It facilitates the compilation of Python code into a format that can be distributed."
            }
        }

        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests using pytest."
                echo "Pytest is a testing framework that enables the creation of straightforward and scalable test cases."
                echo "Pytest is responsible for managing integration tests, which verify the proper functioning of different components of the code when they are combined."
            }
            post {
                success {
                    timeout(time: 30, unit: 'SECONDS') {
                        script {
                            emailext(
                                subject: "Jenkins Job - Unit and Integration Tests SUCCESS",
                                body: "The Unit and Integration Tests stage completed successfully. Please find the attached logs.",
                                to: "soohx0007@gmail.com",  
                                attachLog: true,
                                timeout: 100
                            )
                        }
                    }
                }
                failure {
                    timeout(time: 30, unit: 'SECONDS') {
                        script {
                            emailext(
                                subject: "Jenkins Job - Unit and Integration Tests FAILURE",
                                body: "The Unit and Integration Tests stage failed. Please find the attached logs.",
                                to: "soohx0007@gmail.com",  
                                attachLog: true,
                                timeout: 100
                            )
                        }
                    }
                }
            }
        }

        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo "Analyzing the code quality using Pylint."
                echo "Pylint is a tool for static code analysis that examines your Python code to identify errors."
                echo "It guarantees compliance with coding standards, detects code smells, and proposes enhancements."
            }
        }

        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo "Performing a security scan using Bandit."
                echo "Bandit is a security-focused static analysis tool for Python projects."
                echo "The purpose of this tool is to examine the code in order to identify prevalent security concerns, such as weaknesses in dependencies."
            }
            post {
                success {
                    timeout(time: 30, unit: 'SECONDS') {
                        script {
                            emailext(
                                subject: "Jenkins Job - Security Scan SUCCESS",
                                body: "The Security Scan stage completed successfully. Please find the attached logs.",
                                to: "soohx0007@gmail.com",  
                                attachLog: true,
                                timeout: 100
                            )
                        }
                    }
                }
                failure {
                    timeout(time: 30, unit: 'SECONDS') {
                        script {
                            emailext(
                                subject: "Jenkins Job - Security Scan FAILURE",
                                body: "The Security Scan stage failed. Please find the attached logs.",
                                to: "soohx0007@gmail.com",  
                                attachLog: true,
                                timeout: 100
                            )
                        }
                    }
                }
            }
        }

        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a staging server using Ansible."
                echo "Ansible streamlines the deployment process by managing the configuration and provisioning of the staging environment."
            }
        }

        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging environment using pytest."
                echo "These tests verify the proper functioning of the complete system in an environment that closely resembles production conditions."
                echo "Pytest facilitates the detection of integration issues through the use of automated tests, hence preventing their occurrence during the deployment to production."
            }
        }

        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to the production server (AWS EC2 instance)."
                echo "Ansible guarantees a seamless and automated deployment procedure by implementing the required configurations to the production environment."
                echo "After being deployed, the application will be operational and available to users in the production environment."
            }
        }
    }
}
