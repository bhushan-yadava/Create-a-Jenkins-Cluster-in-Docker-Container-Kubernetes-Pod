FROM ubuntu:22.04

# Install dependencies
RUN apt-get update && \
    apt-get install -y openjdk-17-jdk git curl unzip && \
    useradd -m -s /bin/bash jenkins

# Set environment variables
ENV HOME=/home/jenkins
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64

# Create Jenkins workspace
RUN mkdir -p /home/jenkins/agent
WORKDIR /home/jenkins/agent

# Switch to Jenkins user
USER jenkins

# Default command (keeps container alive — overridden by Jenkins)
CMD ["sleep", "infinity"]

