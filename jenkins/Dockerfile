FROM jenkins/jenkins:lts
USER root

# Install required packages
RUN apt-get update && \
    apt-get install -y \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg2 \
        software-properties-common

# Add the Docker GPG key
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -

# Add the Docker repository to the sources list
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"

# Install Docker CE
RUN apt-get update && \
    apt-get install -y \
        docker-ce \
        docker-ce-cli \
        containerd.io && \
    curl -L https://github.com/jenkinsci/plugin-installation-manager-tool/releases/download/2.12.9/jenkins-plugin-manager-2.12.9.jar -o jenkins-plugin-manager.jar

# Install Docker Compose
RUN curl -L "https://github.com/docker/compose/releases/download/latest/docker-compose-$(uname -s|tr '[:upper:]' '[:lower:]')-$(uname -m)" -o /usr/local/bin/docker-compose
RUN chmod +x /usr/local/bin/docker-compose

# Add the Jenkins user to the Docker group
RUN usermod -aG docker jenkins

# Switch to the Jenkins user
USER jenkins

# Install specified Jenkins plugins
COPY jenkins/plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN java -jar jenkins-plugin-manager.jar --plugin-file /usr/share/jenkins/ref/plugins.txt