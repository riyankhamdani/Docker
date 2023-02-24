Create Kubernetes Manifests files Quickly

Use Kubectl Dry Run
You can create the manifests using the kubectl imperative commands. There is a flag called --dry-run that helps you create the entire manifest template.

Examples
Below are the examples to generate the YAML will using kubectl.

Pod Manifest
Create a pod manifest named firstpod which uses the nginx image
$ kubectl run firstpod --image=nginx --labels app=nginx --dry-run client -o yaml > firstpod.yaml

Create Pod service Manifest file
Generate manifest for a Pod Service that exposes a NodePort. This will only work if you have a running pod.
$ kubectl expose pod firstpod --port=80 --name firstpod-service --type=NodePort --dry-run=client -o yaml > firstpod-service.yaml

Create NodePort service manifest
$ kubectl create service nodeport firstpod --tcp=80:80 --node-port=31001 --dry-run=client -o yaml > firstpod-nodeport.yaml

Create Deployment manifest
Generate deployment with name firstdeploy with nginx image.
$ kubectl create deployment firstdeploy --image=nginx --dry-run=client -o yaml > firstdeploy.yaml

Create Deployment Service Manifest
We can create the deployment service file for deployment firstdeploy which is using NodePort with service port 80.
$ kubectl expose deployment firstdeploy --type=NodePort --port=80 --name=firstdeploy-nodeport --dry-run=client -o yaml > firstdeploy-np.yaml

Create Job and cron-job manifest
Create job named myjob with busybox image.
$ kubect create job myjob --image=busybox:latest --dry-run=client -o yaml > myjob.yaml

Generate cronjob named mycronjob with alpine image and corn schedule.
$ kubectl create cronjob mycronjob --image=alpine:latest --schedule="* * * * *" --dry-run=client -o yaml > mycronjob.yaml

These are some of the generic kubectl. For example, you can add more parameters to make in more configurable as per your requirements. You can add an alias for kubectl as well to reduce the command size by just adding the below lines to .bashrc files
alias k=kubectl
alias kdr='kubectl --dry-run=client -o yaml'
