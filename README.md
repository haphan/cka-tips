# cka-tips

### Training and labs: 

  1. Udemu CKA with practice tests from Mumshad (1 Days).
     - Do once end-to-end if have no perior experience with k8s. If not clear, fill the gap using the list below
     - Do it again before exam day. Time boxed to 50% of allowed time in the lab (1day)

  2. Create your own k8s lab using virtualbox and kubeadm.
     - Excercise: Bootstrap cluster, adding/removing worker nodes, upgrade, change config files kube-apiserver and kubelet, backup-restore etcd

  3. RTFM
     - Exam handbook https://training.linuxfoundation.org/wp-content/uploads/2019/05/CKA-CKAD-Candidate-Handbook-v1.2-.pdf
     - Curriculum https://github.com/cncf/curriculum/raw/master/CKA_Curriculum_v1.19.pdf

  3. (Don't) Kubernetes the hard way from Kelsey Hightower
     - Too informative for the purpose of passing the exam. Good if you want to understand how to manually bootstrap control plane and workers.
     - Not very relevant to the exam since handbook askes to use kubeadm

### Reading list to fill the gap and Exam readiness points:

1. Create control plane, join worker nodes, upgrade kubeapi and kubectl version
   - https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/
   - https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/


2. Adding Network Plugin
   - Remember this page to find network plugin since you cannot visit 3rd party website during the exam
   - https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/

```bash
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
```

3. Kubelet  config file location? How to schedule static pod?
  - https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/
  - https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/kubelet-integration/


4. Etcd back up and restore.  
  - https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/
  - How do we verify the backup is correct?
  - How to quickly find the etcd endpoint and correct cert?  (Tips: ps aux kube-apiserver | grep etcd )

5. Must be very familar and comfortable using jsonpath to output to text file (3-4 questions on this topic)
   - See https://kubernetes.io/docs/reference/kubectl/cheatsheet/


6. Can you do almost everything using kubectl? 
   - Create pod, deployment, daemonset, service, pv, pvc, role, assign role, pull secrets?
   - Tips:  `kubectl create ... -o yaml --dry-run | tee file.yaml `
	  
	  
7. Application deployment management
   - Deployment rollout and rollback
   - Deployment strategies
   - Scale deployment using --replicas
   - Define resource limit and resource request.
   - Anti-affinity rules (Just remember which page to copy from in the docs)
