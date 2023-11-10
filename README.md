# PHP demo using DevSpace

1. Install DevSpace
```
# AMD64
curl -L -o devspace "https://github.com/loft-sh/devspace/releases/latest/download/devspace-linux-amd64" && sudo install -c -m 0755 devspace /usr/local/bin

# ARM64
curl -L -o devspace "https://github.com/loft-sh/devspace/releases/latest/download/devspace-linux-arm64" && sudo install -c -m 0755 devspace /usr/local/bin
```
2.    Initialize Your Project , Run this command in your project directory to create a devspace.yaml config file for your project:
```
git clone https://github.com/jkhazri/OC-demo-devspace.git
cd OC-demo-devspace
devspace init
```
3. DevSpace's initialization wizard will walk you through the setup of the project
```
oc@oc-Vostro-3888:~$ git clone https://github.com/jkhazri/OC-demo-devspace.git
Cloning into 'OC-demo-devspace'...
remote: Enumerating objects: 24, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (21/21), done.
remote: Total 24 (delta 5), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (24/24), 7.08 KiB | 3.54 MiB/s, done.
oc@oc-Vostro-3888:~$ cd OC-demo-devspace
oc@oc-Vostro-3888:~/OC-demo-devspace$ devspace init


     %########%      
     %###########%       ____                 _____                      
         %#########%    |  _ \   ___ __   __ / ___/  ____    ____   ____ ___ 
         %#########%    | | | | / _ \\ \ / / \___ \ |  _ \  / _  | / __// _ \
     %#############%    | |_| |(  __/ \ V /  ____) )| |_) )( (_| |( (__(  __/
     %#############%    |____/  \___|  \_/   \____/ |  __/  \__,_| \___\\___|
 %###############%                                  |_|
 %###########%


info Detecting programming language...

? Select the programming language of this project php

? How do you want to deploy this project? kubectl

? Please enter the paths to your Kubernetes manifests (comma separated, glob patterns are allowed, e.g. 'manifests/**' or 'kube/pod.yaml') [Enter to abort] .

? Do you want to develop this project with DevSpace or just deploy it?  [Use arrows to move, type to filter] I just want to deploy this project

? Which port is your application listening on? (Enter to skip) 

done Project successfully initialized
info Configuration saved in devspace.yaml - you can make adjustments as needed
         
You can now run:
1. devspace use namespace - to pick which Kubernetes namespace to work in
2. devspace dev - to start developing your project in Kubernetes

Run `devspace -h` or `devspace [command] -h` to see a list of available commands and flags

oc@oc-Vostro-3888:~/OC-demo-devspace$ 
```
4. You have succesfully initialized your first DevSpace project.
   After running devspace init, you will see 3 changes in your project :
- New file devspace.yaml (tells DevSpace how this project should be build, deployed, and developed)
- New file devspace_start.sh (is used to show information to the user when the terminal for the dev container opens)
- Added .devspace/ folder (the .devspace/ folder is used by DevSpace to store some information locally when you are working with this project)
