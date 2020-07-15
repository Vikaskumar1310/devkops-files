FROM centos
RUN yum install java-11-openjdk.x86_64 -y
RUN yum install sudo -y
RUN sudo yum install wget -y
RUN sudo install git -y
RUN sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
RUN sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
RUN yum install initscripts.x86_64 -y
RUN yum install jenkins -y
RUN echo -e "jenkins ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
CMD /etc/rc.d/init.d/jenkins start && /bin/bash

RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
RUN chmod +x ./kubectl
RUN cp ./kubectl /usr/bin
RUN mv ./kubectl /usr/local/bin/kubectl
RUN mkdir /root/.kube
COPY client.key /root/.kube
COPY client.crt /root/.kube
COPY ca.crt /root/.kube
COPY config /root/.kube

