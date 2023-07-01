# kubeplugin
Bash script for use as kubectl plugin

`kubeplugin` could be run either as script or as Kubernetes plugin

### Singleton script
Before running ensure that `kubeplugin` file is executable. Or just run

```bash
sudo chmod +x ./scripts/kubeplugin
./scripts/kubeplugin pod argocd
```
Script is written for two types of K8s resources. Either `pod` or `node`

### Response example
```
Resource: pod
Namespace: argocd
Name: argocd-application-controller-0
CPU: 1m
Memory: 34Mi 

Resource: pod
Namespace: argocd
Name: argocd-applicationset-controller-69dbc8585c-szft4
CPU: 1m
Memory: 19Mi 

Resource: pod
Namespace: argocd
Name: argocd-dex-server-59f89468dc-t5qsq
CPU: 1m
Memory: 28Mi 

Resource: pod
Namespace: argocd
Name: argocd-notifications-controller-55565589db-5r69r
CPU: 1m
Memory: 30Mi 

Resource: pod
Namespace: argocd
Name: argocd-redis-74cb89f466-f85ck
CPU: 2m
Memory: 5Mi 

Resource: pod
Namespace: argocd
Name: argocd-repo-server-68444f6479-zfcx6
CPU: 1m
Memory: 38Mi 

Resource: pod
Namespace: argocd
Name: argocd-server-579f659dd5-cdm6n
CPU: 1m
Memory: 42Mi 
```

### `kubectl` plugin
Official documentation how to extend kubectl with plugins you can find
[here](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/)

Create a folder for your `kubectl` plugins 
```bash
mkdir ~/kubectl_plugins
 ```

Edit `.bashrc` in your home directory and add the following line
```
export PATH="~/kubectl_plugins:$PATH"
```

Source your `.bashrc` file or restart the terminal
```bash
source ~/.bashrc
```

Copy the script into the plugins folder and prefix plugin name with `kubectl-`
```bash
cp ./scripts/kubeplugin ~/kubectl_plugins/kubectl-info
```

Make all plugins executable
```bash
sudo chmod +x ~/kubectl_plugins/*
```

Ensure that the plugin is in the list
```bash
kubectl plugin list
```

Run the plugin
```bash
kubectl info pod kube-system
```