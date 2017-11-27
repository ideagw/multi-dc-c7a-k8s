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

#git clone https://github.com/rakeshJn/multi-dc-c7a-k8s.git

cd mu*

# kubectl -n c7a create -f service.yaml
service "cassandra" created

# kubectl -n c7a create -f local_pvs.yaml
persistentvolume "cassandra-data-a" created
persistentvolume "cassandra-data-b" created
persistentvolume "cassandra-data-c" created
persistentvolume "cassandra-data-d" created
persistentvolume "cassandra-data-e" created
persistentvolume "cassandra-data-f" created

# kubectl -n c7a create -f statefulset-a.yaml
statefulset "cassandraa" created

# kubectl -n c7a get pods
NAME           READY     STATUS              RESTARTS   AGE

cassandraa-0   0/1       ContainerCreating   0          59s

# kubectl -n c7a describe pod cassandraa-0

# kubectl -n c7a get pods
NAME           READY     STATUS    RESTARTS   AGE

cassandraa-0   1/1       Running   0          1m

# kubectl -n c7a create -f statefulset-b.yaml

# kubectl -n c7a get statefulsets
NAME         DESIRED   CURRENT   AGE

cassandraa   1         1         3m

cassandrab   1         1         23s

# kubectl -n c7a get pods -o wide
NAME           READY     STATUS    RESTARTS   AGE       IP          NODE

cassandraa-0   1/1       Running   0          7m        10.32.0.3   kube-vm0

cassandrab-0   1/1       Running   0          7s        10.44.0.1   kube-vm1

