kubectl apply -f rbac.yml

kubectl apply -f pv.yml

kubectl apply -f test.yml

# mkdirs on the PV

ml Java/1.8.0_92

./nextflow kuberun KevinSayers/rnaseq-nf -v nfs:/newtest

# nodepools

gcloud container node-pools create highmem --machine-type=n1-standard-1 --cluster=newtest --zone us-central1-a --num-nodes 1

kubectl get pods -o wide


Other ideass:
https://stackoverflow.com/questions/51212904/kubernetes-pvc-with-readwritemany-on-aws
https://gitlab.com/gitlab-org/gitlab-ce/issues/41619

https://yangfan2010.wordpress.com/2018/09/26/nextflow-with-azure-kubernetes-service-aks-a-tutorial-with-working-pipeline/
