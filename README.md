Argo CD is a Git Hub continous delivery tools.Built for Kubernetes efficiency with Github principle

CD is implemented in a typicall microservice app via k8s cluster - any change in app code due to bug fix or code change, ci pipeline in jenkin is triggered-test build and create a new imagee in docker. This image is pushed into repo where it gets pulled into k8s clusterd. We then update the yaml files  and the new repo is applied in K8s. same is repeated for deployment.

The challenge: 
	-many installation and configuration required in Jenkins up to K8s-complex work flow makes infrastructure subject to error 
	-Credentials are exposed in Jenkin, k8s and cloud platforms- exposing your cluster to security risk. 
	Once Jenkins executes changes to k8s configuration (Kubectl deploy) it no longer sees the status of ur deployment. 
	All these is addressed in Argo CD to improve CD.

	The solution from ArgoCD.
	=================
	Rather than access the cluster externally ArgoCD is inbuilt in the cluster, rather than the push trigger that Jenkins adopts, a pull request is made by Argo CD once theres a change to the config file in the repo/ Kubes manifest file.
	Here also the souce code file is in separate repo from the app Config file repo. Jenkins looses sight of happenings in deployment once theres a change in Kubes manifest but Argo CD is configured to see this once it happens and the change is auto pulled from Git in the cluster 
	
	Benefit: 
	-K8s access control with Git - You can set ur git repo to be accessible to everyone- they can all make pull request but they will need superior to approve their changes before the merge takes place. As such u dont need to give ur access to outsiders.
	-Extends the functionality of K8s
 - Visualize your deployment with interactive dashboard.

 ARGO CONFIGURATION:
	- Deploy into cluster using yaml file (IAAC)Create a namespace for ArgoCD
	$kubectl create namespace argocd.

	Install ArgoCD using the command 
	$kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml.

	Verify that the ArgoCD pods are running by using the command 
	$kubectl get pods -n argocd.

	Expose the ArgoCD service by running kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'.

	Obtain the NodePort for the ArgoCD service by using kubectl get svc argocd-server -n argocd -o jsonpath='{.spec.ports[0].nodePort}'.

	Get the Minikube IP address by using minikube ip.

	Access the ArgoCD web interface using the Minikube IP address and the previously obtained NodePort.

	To log in, use the username admin and the generated password for ArgoCD.

	After following these steps, you should be able to use ArgoCD to deploy and manage your applications on your Minikube cluster.

 
