# openshift-install-lab



    sudo -i
    echo ${GUID}

### Install AWS CLI

    # Download the latest AWS Command Line Interface
    curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
    unzip awscli-bundle.zip

    # Install the AWS CLI into /bin/aws
    ./awscli-bundle/install -i /usr/local/aws -b /bin/aws

    # Validate that the AWS CLI works
    aws --version

    # Clean up downloaded files
    rm -rf /root/awscli-bundle /root/awscli-bundle.zip
    
### OpenShift Installer

    OCP_VERSION=4.5.13
    wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/${OCP_VERSION}/openshift-install-linux-${OCP_VERSION}.tar.gz
    tar zxvf openshift-install-linux-${OCP_VERSION}.tar.gz -C /usr/bin
    rm -f openshift-install-linux-${OCP_VERSION}.tar.gz /usr/bin/README.md
    chmod +x /usr/bin/openshift-install


### Openshift CLI

    wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/${OCP_VERSION}/openshift-client-linux-${OCP_VERSION}.tar.gz
    tar zxvf openshift-client-linux-${OCP_VERSION}.tar.gz -C /usr/bin
    rm -f openshift-client-linux-${OCP_VERSION}.tar.gz /usr/bin/README.md
    chmod +x /usr/bin/oc

### Check

    ls -l /usr/bin/{oc,openshift-install}

### OC bash completion

    oc completion bash >/etc/bash_completion.d/openshift



### AWS credentials

See aws-cred.sh

And test...

    aws sts get-caller-identity
        
   
   ### Create SSH key

    ssh-keygen -f ~/.ssh/cluster-${GUID}-key -N ''



### Install OCP

    openshift-install create cluster --dir $HOME/cluster-${GUID}
