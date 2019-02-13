FROM jenkins/jenkins:2.136
USER root
ENV http_proxy=http://proxy.ebiz.verizon.com:80
ENV https_proxy=http://proxy.ebiz.verizon.com:80
ENV no_proxy=10.118.6.35,10.96.0.1,169.254.169.254,*.verizon.com,localhost,*.vzbi.com
ENV JENKINS_OPTS --prefix=/jenkins
#Pre-Install Jenkins Plugins
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

#Installing Docker
RUN apt-get update && apt-get install software-properties-common apt-transport-https ca-certificates -y; \
curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -;\
add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/debian  $(lsb_release -cs) stable";\
apt-get update && apt-get install docker-ce -y

#Installing kubectl from Docker
RUN curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -;\
touch /etc/apt/sources.list.d/kubernetes.list;\
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list;\
apt-get update && apt-get install -y kubectl

# Grant jenkins user group access to /var/run/docker.sock
RUN addgroup --gid 1001 dsock
RUN gpasswd -a jenkins dsock 
USER root
