# multi-dc-c7a-k8s

kubectl get nodes
NAME       STATUS    ROLES     AGE       VERSION
kube-vm0   Ready     master    7m        v1.8.4
kube-vm1   Ready     <none>    3m        v1.8.4


# kubectl label nodes kube-vm0 dc=DC1
node "kube-vm0" labeled
# kubectl label nodes kube-vm1 dc=DC2
node "kube-vm1" labeled


# kubectl get nodes --show-labels
NAME       STATUS    ROLES     AGE       VERSION   LABELS
kube-vm0   Ready     master    12m       v1.8.4    beta.kubernetes.io/arch=amd64,beta.kubernetes.io/os=linux,dc=DC1,kubernetes.io/hostname=kube-vm0,node-role.kubernetes.io/master=
kube-vm1   Ready     <none>    8m        v1.8.4    beta.kubernetes.io/arch=amd64,beta.kubernetes.io/os=linux,dc=DC2,kubernetes.io/hostname=kube-vm1


# kubectl create namespace c7a

