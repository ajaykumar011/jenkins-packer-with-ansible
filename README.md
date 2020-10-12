```
            ___        ______    _   _ _____   ____            _
           / \ \      / / ___|  | \ | | ____| |  _ \ __ _  ___| | _____ _ __
          / _ \ \ /\ / /\___ \  |  \| |  _|   | |_) / _` |/ __| |/ / _ \ '__|
         / ___ \ V  V /  ___) | | |\  | |___  |  __/ (_| | (__|   <  __/ |
        /_/   \_\_/\_/  |____/  |_| \_|_____| |_|   \__,_|\___|_|\_\___|_|

```

[![Circle CI](https://circleci.com/gh/rosstimson/awsne-packer.svg?style=svg)](https://circleci.com/gh/rosstimson/awsne-packer)

## Setup

* Git clone this project:
    Original: `https://github.com/rosstimson/awsne-packer.git`
    Working : 'https://github.com/ajaykumar011/jenkins-packer-with-ansible.git'

# install terraform
wget -q https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip \
&& unzip -o terraform_${TERRAFORM_VERSION}_linux_amd64.zip -d /usr/local/bin \
&& rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip

# install packer

# Download Location (method-1 - used in this example) :
# https://www.packer.io/downloads.html

cd /usr/local/bin
wget -q https://releases.hashicorp.com/packer/0.10.2/packer_0.10.2_linux_amd64.zip
unzip packer_0.10.2_linux_amd64.zip
packer --version

#Method -2 (Ubuntu/Debian)

curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install packer


#Method -2 (Amazon Linux 2)

sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install packer

# clean up
apt-get clean
rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip
rm packer_0.10.2_linux_amd64.zip


### AWS Credentials

AWS credentials needed should be stored in the following environment variables:

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`

An example IAM policy for the Packer user is supplied:
`packer-iam-policy.example.json`

## Build AMI

Building an EC2 AMI is as simple as:

* `packer build awsne-packer.json`
* Grab a coffee.

## Authors

Ross Timson <ross@rosstimson.com>
