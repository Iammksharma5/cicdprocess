pipeline:
  agent: any

  environment:
    WEBHOOK_TOKEN: ${JENKINS_CREDENTIALS_WEBHOOK_SECRET_TOKEN}

  triggers:
    - genericTrigger:
        causeString: "Triggered by GitHub Webhook"
        token: "${WEBHOOK_TOKEN}"  # Using environment variable for security
        printContributedVariables: true
        printPostContent: true

  stages:
    - stage: "Checkout Code"
      steps:
        - script: |
            git branch: 'main'
            git url: 'https://github.com/Iammksharma5/cicdprocess.git'

    - stage: "Trigger Freestyle Jobs"
      steps:
        - script: |
            def jobs = ['Project-1', 'Project-2', 'Project-3', 'Project-4', 'Project-5']
            for (job in jobs) {
              echo "Triggering Job: ${job}"
              def result = build job: job, wait: true, propagate: true
              echo "${job} completed with status: ${result.getResult()}"
            }

  post:
    success:
      - script: echo "All jobs executed successfully!"
    failure:
      - script: echo "One or more jobs failed."
