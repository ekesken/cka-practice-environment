FROM arush/gateone:latest
RUN apt-get update \
        && apt-get remove docker docker-engine docker.io containerd runc \
        && apt-get -y install wget curl vim openssh-client iputils-ping telnet netcat nmap sudo vim dbus apt-transport-https ca-certificates gnupg-agent \
                software-properties-common bash-completion cgroup-bin cgroup-lite libcgroup1 \
        && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - \
        && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" \
        && curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add - \
        && add-apt-repository "deb [arch=amd64] https://apt.kubernetes.io kubernetes-xenial main" \
        && apt-get update \
        && apt-get -y install docker-ce=5:18.09.9~3-0~ubuntu-xenial docker-ce-cli=5:18.09.9~3-0~ubuntu-xenial containerd.io kubelet kubeadm kubectl \
	# && curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
	# && chmod +x ./kubectl \
	# && mv ./kubectl /usr/local/bin/kubectl \
	&& ssh-keygen -N "" -t rsa -f ~/.ssh/id_rsa \
        && cat ~/.ssh/id_rsa.pub > ~/.ssh/authorized_keys \
	&& apt-get clean all
COPY etc/ /etc/
RUN systemctl enable gateone
CMD [ "/sbin/init" ]
