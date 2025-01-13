https://madhuakula.com/kubernetes-goat/docs/

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"


```
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.32/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
sudo chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg # allow unprivileged APT programs to read this keyring
```


Install using native package management


sudo apt-get update
# apt-transport-https may be a dummy package; if so, you can skip that package
```
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg
Download the public signing key for the Kubernetes package repositories. The same signing key is used for all repositories so you can disregard the version in the URL:
```


# If the folder `/etc/apt/keyrings` does not exist, it should be created before the curl command, read the note below.
# sudo mkdir -p -m 755 /etc/apt/keyrings
```
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.32/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
sudo chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg # allow unprivileged APT programs to read this keyring
Note:
In releases older than Debian 12 and Ubuntu 22.04, folder /etc/apt/keyrings does not exist by default, and it should be created before the curl command.
Add the appropriate Kubernetes apt repository. If you want to use Kubernetes version different than v1.32, replace v1.32 with the desired minor version in the command below:
```


# This overwrites any existing configuration in /etc/apt/sources.list.d/kubernetes.list
```
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.32/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo chmod 644 /etc/apt/sources.list.d/kubernetes.list   # helps tools such as command-not-found to work correctly
Note:
To upgrade kubectl to another minor release, you'll need to bump the version in /etc/apt/sources.list.d/kubernetes.list before running apt-get update and apt-get upgrade. This procedure is described in more detail in Changing The Kubernetes Package Repository.
Update apt package index, then install kubectl:

sudo apt-get update
sudo apt-get install -y kubectl
```
