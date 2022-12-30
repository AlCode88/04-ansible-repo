# Install Ansible on Rhel 8
```
#!/bin/bash
sudo subscription-manager register
sudo subscription-manager repos --enable ansible-2.9-for-rhel-8-x86_64-rpms
sudo yum install ansible
```
# Install Ansible on Amazo Linux 2
1. Update repository
```
sudo yum update -y
```
2. Install packages
```
amazon-linux-extras install ansible2 -y
```
3. Verify installation
```
ansible --version
```
4. Check package installation by running:
```
ansible rpm -qa | grep ansible
```
## Install the same package with Epel
5. You can remove the package that you install with amazon-linux-extras by running:
```
sudo yum remove ansible
```
6. Disable amazon linux extras repository since it takes high pirority then our epel
```
amazon-linux-extras disable ansible2
``` 
7. Install epel packages
```
amazon-linux-extras install epel -y
```
8. Enable epel repository
```
yum-config-manager --enable epel   # verify if enabled sign is true
```
9. You can verify installation of epel by running
```
yum repolist
```
10. Install ansible with epel
```
sudo yum install ansible -y 
```
11. Or you can run by enabled flag to make sure
```
yum --enablerepo epel install ansible -y
```
# Install Ansible on MacOS
- We need to use Homebrew Package Manager
- Alternatively you can use PIP but you need to download a software and complie a source code

1. Install brew you need to go ot oficial brew webpage
2. Check the version
```
brew --version
```
3. You can look for ansible packages in brew by running command
```
brew search ansible
```
4. Install ansible on macos with brew
```
brew install ansible
```
5. Check the version of the ansible
```
ansible --version
```
## If you want to install specific ansible version with brew
1. Check the all available versions
```
brew search ansible
```
2. You need to remove the old installed version
```
brew remove ansible
```
3. Install ansible 2.9
```
brew install ansible@2.9
```
4. It will be added to path
```
/usr/local/opt/ansible@2.9/bin
```
5. check the ansible version
```
/usr/local/opt/ansible@2.9/bin/ansible --version
```
# Install ansible with PIP - python package manager
pip is a package manager for Python. It is used to install and manage packages (libraries and tools) that are written in Python.

With pip, you can install packages from the Python Package Index (PyPI) and other package indexes. You can also use pip to install packages from local project directories, version control repositories, and other sources.

To use pip, you will need to have Python installed on your system. If you do not have Python installed, you can download it from the official Python website. Once you have Python installed, you can use the pip command in your command prompt or terminal to install packages. If you want to use latets release of ansible you need to use pip.
1. Example on how to install any packages
```
pip install package_name
```
2. Example to update and remove packages
```
pip install --upgrade package_name
pip uninstall package_name
```
## Install package 
1. First we need to upgrage the pip version
```
python3 -m pip install --upgrade pip --user
```
2. Install ansible with pip
```
python3 -m pip install --user ansible
```
3. Check the version of ansible
```
ansible --version
```
