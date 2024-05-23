---
tags:
  - note
  - learning
  - procedure
related: 
timestamp: "202405011811"
---

# PySpark Notebook via Azure VM

1. Install docker on the VM following this [guide](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04).
2. Create the Dockerfile 
	```Dockerfile
	# Use the official Jupyter image as a parent image
	FROM jupyter/base-notebook
	
	# Install OpenJDK for Spark
	USER root
	RUN apt-get update && apt-get install -y openjdk-11-jdk-headless
	
	# Set JAVA_HOME environment variable
	ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64
	ENV PATH $PATH:$JAVA_HOME/bin
	
	# Install Python 3 and PySpark
	RUN pip install pyspark==3.1.1
	
	# Switch back to the jovyan user
	USER jovyan
	
	# Expose the Jupyter port
	EXPOSE 8888
	
	# Start the Jupyter Notebook
	CMD ["start-notebook.sh", "--NotebookApp.token=''", "--NotebookApp.password=''"]
	```
	- Then, build the Docker image with `docker build -t pyspark-jupyter .`
3. Run Docker container ensuring port forwarding (port 8888 is forwarded to port 8888) between the VM and the Docker container
	```bash
	docker run -p 8888:8888 -v /path/to/your/data:/home/jovyan/data pyspark-jupyter
	```
	- The `-v` option mounts the directory `/path/to/your/data` from your host to `/home/jovyan/data` in the container, allowing your notebooks to access files stored on your host machine.
4. Configure the VM’s Firewall
	- Ensure that the firewall on the VM allows traffic on the port Jupyter is using (i.e. 8888).
5. Access the VM via SSH from the local machine, with port forwarding (port 8888 of the local machine forwarded to port 8888 of the VM).
	- This will create a tunnel from port 8888 of the local machine to port 8888 of the Docker container.
	```bash
	ssh -i path/to/private_key -L 8888:localhost:8888 user@ip_address 
	```
1. Open the browser on the local machine and connect to http://localhost:8888

--- 
# References
