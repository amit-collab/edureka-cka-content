## Calico pod network
```
	sudo kubeadm init
		Note: note down the kubeadm join command 

	sudo mkdir -p $HOME/.kube
	sudo rm $HOME/.kube/config
	sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
	sudo chown $(id -u):$(id -g) $HOME/.kube/config

	sudo kubectl apply -f https://docs.projectcalico.org/v3.8/manifests/calico.yaml
```
## how to find kubeadm join token later
```
token=`kubeadm token generate`
kubeadm token create "$token" --print-join-command --ttl=0
```
















































## Flannel pod network
```
	sudo kubeadm init --apiserver-advertise-address=<master ip> --pod-network-cidr=10.244.0.0/16
	
	sudo mkdir -p $HOME/.kube
	sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
	sudo chown $(id -u):$(id -g) $HOME/.kube/config

	make note of kubeadm join command to be run on Nodes
	
	for coredns pods to come up run below
		kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/2140ac876ef134e0ed5af15c65e414cf26827915/Documentation/kube-flannel.yml
```
