# INSTRUCTIONS FOR SPRING PET CLINIC JENKINS PROJECT:

1. New jenkinsfile: Jenkins pipeline will:
    1.1 clone the github repository,
    1.2 build,
    1.3 execute test,
    1.4 package,
    1.5 image build,
    1.6 push to artifactory
2. New Dockerfile: docker file for image creation
3. updated pom.xml: pom.xml modified to resolve dependecies from JCenter repositiory
4. Artifactory - push jar to Artifactory

* update
    ARTIFACTORY_URL
    ARTIFACTORY_USER_NAME
    ARTIFACTORY_PASSWORD
    ARTIFACTORY_TARGET_REPO
  with your Artifactory credentials, URL  & target repo

# Important:
1. If you installed jenkins-lts on a Mac using brew, then please use this file to update the above environment variables for jenkins:

  /usr/local/Cellar/jenkins-lts/2.263.1/homebrew.mxcl.jenkins-lts.plist

  Here is an example:

  <key>ARTIFACTORY_TARGET_REPO</key>
    <string>example-repo-local</string>

  Also use the file to point jenkins to a different port, for example:
        <string>--httpPort=7070</string>

2. Then, restart jenkins service, for these environment variables to take effect:
  brew services restart jenkins-lts

3. Then, confirm them in Jenkis System Info environment variables page

# How to run the project?

1. Execution of pipeline creates a docker image 'my-spring-pet-clinic-boot-image'
2. Use this command to run the project:

      docker run -p 8080:8080 my-spring-pet-clinic-boot-image

3. Access webpage by http://localhost:8080
