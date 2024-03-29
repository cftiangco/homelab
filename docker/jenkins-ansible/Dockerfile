FROM jenkins/jenkins:latest

USER root

# Install dependencies for virtual environment creation
RUN apt-get update && apt-get install -y python3-venv

# Create a virtual environment with Python 3
WORKDIR /app
RUN python3 -m venv /app/venv
ENV PATH="/app/venv/bin:$PATH"

# Install Ansible (upgraded) within the virtual environment
RUN pip install --upgrade ansible

# Switch to Jenkins user for container runtime
USER jenkins