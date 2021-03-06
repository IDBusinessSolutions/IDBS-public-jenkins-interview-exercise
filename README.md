# IDBS-public-jenkins-interview-exercise

### Problem

Write a Jenkins pipeline to build and test a Java application built using Gradle.

### Requirements

* Build will be set up to run as a multibranch pipeline covering both main branch and pull requests
* The following stages are required:
    * build
    * unit test
    * integration tests
* Integration tests should run on main branch only (not on PRs)
* Integration tests should time out after 30 minutes
* Credentials are required by all stages. Credentials id is `credentials` (secret text) and should be added as a flag to the gradle command (see below)
* Notifications should be sent to the `builds` slack channel when a build has failed, has test failures or is now fixed
* Option to send notification to a different slack channel
* How would we refactor into a shared pipeline?
* How would this pipeline handle custom post success behaviour?


### Supplementary info

* Shared-library folder would normally be in a different repo. Assume this library is implicitely loaded
* Suitable k8s base agent can be used with a label of `gradle`
* To run gradle, the command line is: `./gradlew some_command --no-daemon -Pcredential=credentialValue`
* Gradle commands
    * build - `build`
    * unit test - `test`
    * integration test - `it`
* slack notifications sent as `slackSend message: message, color: colour, channel: slackChannel`
