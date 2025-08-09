FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# Install Java, curl, git
RUN apt-get update && \
    apt-get install -y openjdk-17-jdk wget git curl && \
    useradd -m -s /bin/bash jenkins

# Download Jenkins WAR
RUN wget https://get.jenkins.io/war-stable/latest/jenkins.war -O /home/jenkins/jenkins.war

WORKDIR /home/jenkins

EXPOSE 8080

CMD ["java", "-jar", "jenkins.war"]
