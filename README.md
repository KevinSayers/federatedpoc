# federatedpoc
Exploratory work looking at using Kubernetes Federation to run bioinformatics workflows on multiple distant clusters. 

# Cluster setup
This will create three clusters alpha, beta, and mgmt.

`git clone https://github.com/slateci/minifed`

`cd minifed/`

`./init.sh`

# Add persistent volumes
`git clone https://github.com/KevinSayers/federatedpoc`

`kubectl config use-context alpha`

`kubectl create -f pv.yaml`

`kubectl create -f claim.yaml`

`kubectl config use-context beta`

`kubectl create -f pv.yaml`

`kubectl create -f claim.yaml`

# Running a job 
This will execute the workflow on each of the clusters. Currently the context must be switched manually. Ideally the Job API could be used to submit jobs to the federated cluster as a whole.

`nextflow kuberun KevinSayers/rnaseq-nf -v task-pv-claim:/newtest -profile alpha`

`nextflow kuberun KevinSayers/rnaseq-nf -v task-pv-claim:/newtest -profile beta`

# Next steps
Federate clusters created on different cloud providers. 

