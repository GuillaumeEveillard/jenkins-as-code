FROM jenkins/jenkins:lts

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

RUN /usr/local/bin/install-plugins.sh git:latest docker-workflow:latest workflow-multibranch:latest
