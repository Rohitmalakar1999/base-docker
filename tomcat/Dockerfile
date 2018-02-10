# Copyright 2018 Learnk Arts Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

################## BEGIN INSTALLATION ######################

# pulling the base ubuntu 16.04 after updating the security pataches
FROM learnkarts/java:latest

#FILE AUTHOR
MAINTAINER Ramakrishna Thandra <ramakrishna.thandra@gmail.com>

#ARGUMENTS TO PASSED
ARG TOMCAT_VERSION=8.5.5

#INSTALL MAVEN
RUN apt-get install -y maven
    
#INSTALL TOMCAT
# Here comes the tomcat installation
RUN apt-get -y install wget && \
    groupadd tomcat && \
    useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
    
RUN cd /tmp && \
    wget https://archive.apache.org/dist/tomcat/tomcat-8/v$TOMCAT_VERSION/bin/apache-tomcat-$TOMCAT_VERSION.tar.gz && \
    mkdir /opt/tomcat && \
    tar xzvf apache-tomcat-8*tar.gz -C /opt/tomcat --strip-components=1 && \
    cd /opt/tomcat && \
    chgrp -R tomcat /opt/tomcat && \
    chmod -R g+r conf && \
    chown -R tomcat webapps/ work/ temp/ logs/ 

# Expose the default tomcat port
EXPOSE 8080

# Start the tomcat (and leave it hanging)
CMD ["/opt/tomcat/bin/startup.sh"]
