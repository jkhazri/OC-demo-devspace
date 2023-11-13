# PHP demo using DevSpace
## what you need to check before preparing your deployment

**Important**: 

Please make sure you have enough resources in your Vcluseter before you start your deployment.

**Best practice :** 
You may need to limit your application ressources by adding what we called ResourceQuota kubernetes kind in your deployment Yaml file.

In this example, I've added a ResourceQuota object that sets resource limits for CPU and memory. Adjust the values based on your application's requirements. You can customize the CPU, memory and ather values according to your application's needs and the available resources in your Kubernetes cluster.

If you need to learn more about the ResourceQuota , please refer to this documentation : https://kubernetes.io/docs/concepts/policy/resource-quotas/

```bash
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: php-app-ingress
spec:
  rules:
  - host: docs-vcluster2-443.m1dns.com  # Set the desired domain or hostname here
    http:
      paths:
      - path: /
        pathType: Prefix # type the path that will be used
        backend:
          service:
            name: php-app-clusterip-service
            port:
              number: 20210
---
apiVersion: v1
kind: ResourceQuota
metadata:
  name: ingress-resource-quota
spec:
  hard:
    cpu: "500m"  # 0.5 CPU cores
    memory: "512Mi"  # 512 Megabytes of memory

```
1. Install DevSpace
```bash
# AMD64
curl -L -o devspace "https://github.com/loft-sh/devspace/releases/latest/download/devspace-linux-amd64" && sudo install -c -m 0755 devspace /usr/local/bin

# ARM64
curl -L -o devspace "https://github.com/loft-sh/devspace/releases/latest/download/devspace-linux-arm64" && sudo install -c -m 0755 devspace /usr/local/bin
```
2.    Initialize Your Project , Run this command in your project directory to create a devspace.yaml config file for your project:
```bash
git clone https://github.com/jkhazri/OC-demo-devspace.git
cd OC-demo-devspace
devspace init
```
3. DevSpace's initialization wizard will walk you through the setup of the project
![Alt Text](https://github.com/jkhazri/OC-demo-devspace/blob/main/images/dev-space05.png)


4. You have succesfully initialized your first DevSpace project.
   After running devspace init, you will see some changes in your project :
- New file devspace.yaml (tells DevSpace how this project should be build, deployed, and developed)
- New file devspace_start.sh (is used to show information to the user when the terminal for the dev container opens)  
![Alt Text](https://github.com/jkhazri/OC-demo-devspace/blob/main/images/tree.png)

5. now you are redy to deploy the application using devspace file :
- the ```devspace use context``` command is used to choose the Vcluster context:
   
```bash
devspace use context
? Which context do you want to use? docs-vcluster2
done Successfully set kube-context to 'docs-vcluster2'
```
- the ```devspace use namespace``` command is used to create the namespace (if not my-namespace will be created and then used as default):
  
```bash
devspace use namespace PHP-ns
info The default namespace of your current kube-context 'docs-vcluster2' has been updated to 'PHP-ns'
         To revert this operation, run: devspace use namespace 

done Successfully set default namespace to 'PHP-ns'
```

