# rancher-demo
https://www.linkedin.com/pulse/rancher-kubernetes-engine-rke-installation-cluster-prayag-sangode/ <br />
https://medium.com/@enterco-0/installing-rancher-kubernetes-on-a-single-node-cluster-969584274750 <br />

<br />

yum install -y yum-utils device-mapper-persistent-data lvm2  <br />
yum install -y docker-ce --nobest  <br />
usermod -aG docker kwood <br />
setup authorized keys file <br />
sudoers kwood <br />

<br />

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 <br />
chmod 700 get_helm.sh <br />
./get_helm.sh <br />
helm version <br />

<br />

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" <br />
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl <br />
mv ./kubectl ~/.local/bin/kubectl <br />
kubectl version --client <br />
kubectl version <br />

<br />

curl https://github.com/rancher/rke/releases/download/v1.5.1/rke_linux-amd64 -O <br />
cp rke_linux-amd64 ~/bin/rke <br />
mv rke_linux-amd64 rke <br />
chmod +x rke <br />
mv rke /usr/local/bin <br />
ssh-keygen -t rsa -b 4096 <br />
rke config --name cluster.yml <br />
rke up <br />
mkdir ~/.kube <br />
cp kube_config_cluster.yml /$HOME/.kube/config <br />
kubectl get nodes <br />

