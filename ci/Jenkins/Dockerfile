FROM jenkins/jenkins:lts

USER root
RUN apt-get update -qq \
    && apt-get install -qqy apt-transport-https ca-certificates curl gnupg2 software-properties-common 
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update  -qq \
    && apt-get install docker-ce=17.12.1~ce-0~debian -y
RUN usermod -aG docker jenkins

# USER jenkins

COPY build-my-project_config.xml /var/jenkins_home/jobs/build-my-project/config.xml

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

RUN /usr/local/bin/install-plugins.sh git:latest docker-workflow:latest workflow-multibranch:latest workflow-aggregator:latest
