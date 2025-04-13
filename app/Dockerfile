# Use Ubuntu as the base image
FROM ubuntu:latest

# Install required packages and clean up apt cache to save space
RUN apt-get update && \
    apt-get install -y wget unzip openjdk-11-jdk && \
    rm -rf /var/lib/apt/lists/*  # Remove cached package lists to save space

# Set environment variables
ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH

# Download and Install Tomcat 8.5
RUN wget https://archive.apache.org/dist/tomcat/tomcat-8/v8.5.91/bin/apache-tomcat-8.5.91.tar.gz && \
    tar -xvf apache-tomcat-8.5.91.tar.gz && \
    mv apache-tomcat-8.5.91 /usr/local/tomcat && \
    rm apache-tomcat-8.5.91.tar.gz

# Remove default ROOT directory
RUN rm -rf /usr/local/tomcat/webapps/ROOT

# Copy the correct .war file
COPY dptweb-1.0.war /usr/local/tomcat/webapps/ROOT.war
# Expose the Tomcat port
EXPOSE 8080

# Start Tomcat
CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]
