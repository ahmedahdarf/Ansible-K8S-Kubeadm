ansible-K8S-kubeadm version de k8S 1.21




##Il faut tout d'abord creer la clé pub SSH pour faire communiquer les VMs de maniere securisé

Tester La connectivité avec 
		## ansible all -i hosts -m ping  -k

##Apres creer un utilisateur ubuntu en lui donné les droits de sudo sans mot de passe (voir le fichier initial.yaml )
	## ansible-playbook -i hosts initial.yml -Kk


## Apres installer les dependences de K8S (docker , kubelet, kubeadm, kubectl sur le master)
	## ansible-playbook -i hosts kube-dependencies.yml -Kk


## Apres desactiver le swap(swapoff -a ) et configurer l'operateur network (Calico) et initialiser le cluster (kubeadm init)
	## ansible-playbook -i hosts masters.yml -Kk

## Apres joindre les nodes dans le master 
	## ansible-playbook -i hosts worker.yml -Kk