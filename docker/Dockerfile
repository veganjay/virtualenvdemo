FROM python:latest

# Update system packages
RUN apt update

# Install virtualenv and virtualenv wrapper
RUN python3 -m pip install virtualenv virtualenvwrapper

# Upgrade pip globally
RUN python3 -m pip install --upgrade pip

# Add Python user
RUN useradd -rm -d /home/python -s /bin/bash python 

# Change user
USER python
WORKDIR /home/python

# Update .bashrc
RUN echo "source /usr/local/bin/virtualenvwrapper.sh" >> /home/python/.bashrc

# Copy the bash aliases for venv wrapper
COPY bash_aliases /home/python/.bash_aliases

# Run bash
CMD /bin/bash 
