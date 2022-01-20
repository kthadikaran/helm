# Helm
Helm is the package manager(like apt and yum for linux distribution) for the kubernetes and running on top of the kubernetes.  

## Helm Chart
Helm Charts are simply Kubernetes YAML manifests combined into a single package(It is a collection of all your versioned, pre-configured application resources which can be deployed as one unit.) that can be deployed on the Kubernetes clusters. Once packaged, installing a Helm Chart into your cluster is as easy as running a single helm install, which really simplifies the deployment of containerized applications.  

The directory structure of the helm chart:
```
thadikaran@ubuntu:~$ tree helm_demoapp01/
helm_demoapp01/
├── Chart.yaml
├── charts
├── templates
│   ├── NOTES.txt
│   ├── _helpers.tpl
│   ├── deployment.yaml
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── service.yaml
│   ├── serviceaccount.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml

3 directories, 10 files
```
#### Chart.yaml:  
This is where you put all the information about the chart you are packaging. So, for example, your version number, etc. This is where you will put all those details.  

#### Values.yaml: 
This is where you define all the values you want to inject into your templates. If you are familiar with terraform, think of this as helms variable.tf file.  
#### Charts: 
This is where you store other charts that your chart depends on. You might be calling another chart that your chart need to function properly.  
#### Templates: 
This folder is where you put the actual manifest you are deploying with the chart. For example you might be deploying an nginx deployment that needs a service, configmap and secrets. You will have your deployment.yaml, service.yaml, config.yaml and secrets.yaml all in the template dir. They will all get their values from values.yaml from above.
