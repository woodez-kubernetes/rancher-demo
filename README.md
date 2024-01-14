# rancher-demo
https://www.linkedin.com/pulse/rancher-kubernetes-engine-rke-installation-cluster-prayag-sangode/


https://medium.com/@enterco-0/installing-rancher-kubernetes-on-a-single-node-cluster-969584274750


yum install -y yum-utils device-mapper-persistent-data lvm2  
yum install -y docker-ce --nobest
usermod -aG docker kwood
setup authorized keys file
sudoers kwood


curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
helm version


curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
mv ./kubectl ~/.local/bin/kubectl
kubectl version --client
kubectl version


curl https://github.com/rancher/rke/releases/download/v1.5.1/rke_linux-amd64 -O
cp rke_linux-amd64 ~/bin/rke
mv rke_linux-amd64 rke
chmod +x rke
mv rke /usr/local/bin
ssh-keygen -t rsa -b 4096
rke config --name cluster.yml
rke up
mkdir ~/.kube
cp kube_config_cluster.yml /$HOME/.kube/config
kubectl get nodes

