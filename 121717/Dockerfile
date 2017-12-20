#####THIS IS FOR SCRNASEQ ANALYSIS, CONTAINS SPECIFIC PYTHON AND R PACKAGES AND VERSIONS! 
#####121717 JY
# Use a forked ubuntu runtime as a parent image
FROM phusion/baseimage

# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /home/johnny

# Install any needed packages specified in requirements.txt
RUN apt-get update && \ 
        apt-get install -y nano && \
	apt-get install -y libx11-6 libxrender1 libcairo2-dev
RUN echo "export PATH='/home/johnny/anaconda2/bin:$PATH'" >> ~/.bashrc
RUN echo "alias notebook='jupyter notebook --allow-root --ip 0.0.0.0 --no-browser'" >> ~/.bashrc

# Make port 8888 available to the world outside this container
EXPOSE 8888

# Define environment variable
ENV NAME World

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

######TO RUN JUPYTER NOTEBOOK, RUN CONTAINER WITH: docker run -it -p 8888:8888 image:version
#####THEN RUN 'notebook'
#####THEN ON HOST CAN ACCESS JUPTER NOTEBOOK DIRECTLY AT LOCALHOST:8888/TREE
#####OR CAN ACCESS FROM REMOTE TERMINAL BY USING THIS ALIAS IN .BASHRC FILE:
##### alias notebook_docker="ssh -N -f -L localhost:8890:localhost:8888 johnny@biochem1.ucsf.edu; nohup firefox http://localhost:8890 &"

