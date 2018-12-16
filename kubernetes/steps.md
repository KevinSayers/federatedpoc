gcloud container clusters create newtest --zone us-central1-a --enable-legacy-authorization

gcloud compute disks create --size=10GB --zone us-central1-a gce-nfs-disk

kubectl apply -f nfs.yml 

kubectl apply -f service.yml

kubectl get svc nfs-server

# Note the ip from above cmd

kubectl apply -f pv.yml


kubectl apply -f test.yml

# mkdirs on the PV

kubectl exec -it nfs-busybox-b5c8b95fb-299n7 -- mkdir /data/kevin


nextflow kuberun KevinSayers/rnaseq-nf -v nfs:/newtest

# nodepools

gcloud container node-pools create highmem --machine-type=n1-standard-1 --cluster=newtest --zone us-central1-a

`kubectl get pods -o wide`


Other ideass:
https://stackoverflow.com/questions/51212904/kubernetes-pvc-with-readwritemany-on-aws
https://gitlab.com/gitlab-org/gitlab-ce/issues/41619

https://yangfan2010.wordpress.com/2018/09/26/nextflow-with-azure-kubernetes-service-aks-a-tutorial-with-working-pipeline/
