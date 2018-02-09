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
ARG MAVEN_VERSION=3.3.9

ENV M2_HOME=/opt/maven \
    PATH=${M2_HOME}/bin:${PATH}

#INSTALL MAVEN
RUN apt-get update && \
    apt-get install -y wget && \
    cd /opt && \
    wget http://www-eu.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz && \
    tar -xvzf apache-maven-3.3.9-bin.tar.gz && \
    mv apache-maven-3.3.9 maven
    
#INSTALL TOMCAT

RUN  groupadd tomcat && \
     useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat && \

RUN  cd /opt && \
     wget http://apache.mirrors.ionfish.org/tomcat/tomcat-8/v8.5.5/bin/apache-tomcat-8.5.5.tar.gz && \
     tar -xvzf apache-tomcat-8.5.5.tar.gz && \
     mv apache-tomcat-8.5.5 tomcat && \
     chgrp -R tomcat /opt/tomcat && \
     cd /opt/tomcat && \
     chmod -R g+r conf && \
     chmod g+x conf && \
     chown -R tomcat webapps/ work/ temp/ logs/
     

