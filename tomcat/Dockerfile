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
ARG TOMCAT_VERSION=8.0.49

#INSTALL MAVEN
RUN apt-get install -y maven wget
    
#INSTALL TOMCAT
RUN wget --quiet --no-cookies http://apache.rediris.es/tomcat/tomcat-8/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz -O /tmp/tomcat.tgz && \
    tar xzvf /tmp/tomcat.tgz -C /opt && \
    mv /opt/apache-tomcat-${TOMCAT_VERSION} /opt/tomcat && \
    rm /tmp/tomcat.tgz && \
    rm -rf /opt/tomcat/webapps/examples && \
    rm -rf /opt/tomcat/webapps/docs && \
    rm -rf /opt/tomcat/webapps/ROOT

#ENV SETTIMG TOMCAT
ENV CATALINA_HOME /opt/tomcat
ENV PATH $PATH:$CATALINA_HOME/bin

#EXPOSED PORTS FOR TOMCAT
#EXPOSE 8080
#EXPOSE 8009
VOLUME "/opt/tomcat/webapps"
WORKDIR /opt/tomcat

#LAUNCH TOMCAT
#CMD ["/opt/tomcat/bin/catalina.sh", "run"]
