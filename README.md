# PHP demo using DevSpace

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
   After running devspace init, you will see 3 changes in your project :
- New file devspace.yaml (tells DevSpace how this project should be build, deployed, and developed)
- New file devspace_start.sh (is used to show information to the user when the terminal for the dev container opens)
- Added .devspace/ folder (the .devspace/ folder is used by DevSpace to store some information locally when you are working with this project)
  
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

