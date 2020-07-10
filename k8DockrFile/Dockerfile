FROM centos
RUN yum install java-11-openjdk.x86_64 -y
RUN yum install openssh-server -y
RUN yum install sudo -y
RUN echo "root:redhat" | chpasswd
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

RUN chmod +x ./kubectl
RUN mv ./kubectl /usr/local/bin/kubectl
RUN mkdir /root/.kube
COPY client.key /root/.kube
COPY client.crt /root/.kube
COPY ca.crt /root/.kube
COPY config /root/.kube
RUN mkdir /root/devops
COPY deploy.yml /root/devops
RUN ssh-keygen -A
CMD ["/usr/sbin/sshd", "-D"]Î

