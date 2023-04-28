# Kubeweek-storage
## Create dir and create persistent volume config yaml
mkdir storage
cd storage
vim pv-config.yml
#run below command to create the persistent volume
kubectl create -f pv-config.yml
#it will validate your PV config file and no errors then shows below message on screen
#persistentvolume/my-volume created
#Check the created PV to see if it is available
ubuntu@ip-172-31-89-155:~/storage$ kubectl get pv
NAME        CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS   REASON   AGE
my-volume   3Gi        RWO            Retain           Available                                   6m22s
#Check the description of the PersistentVolume by running kubectl describe command
ubuntu@ip-172-31-89-155:~/storage$ kubectl describe pv my-volume
Name:            my-volume
Labels:          <none>
Annotations:     <none>
Finalizers:      [kubernetes.io/pv-protection]
StorageClass:    
Status:          Available
Claim:           
Reclaim Policy:  Retain
Access Modes:    RWO
VolumeMode:      Filesystem
Capacity:        3Gi
Node Affinity:   <none>
Message:         
Source:
    Type:          HostPath (bare host directory volume)
    Path:          /app/data
    HostPathType:  
Events:            <none>
#As seen above, the PV is available and ready to serve a PVC storage request. The status will change from available to bound when it has been claimed
