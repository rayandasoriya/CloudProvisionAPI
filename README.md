# CSC 519 - DevOps
## HW1

This repository contains the code API from two cloud providers for automatic provision. The two cloud providers are DigitalOcean and Google Cloud Provider. The task was to create two VMs using a registered ssh key and print the IP address of the new server.

### DigitalOcean
The source code of the DigitalOcean part is in Node Js. It consists of the package.json file which consists of all the required node packages for running the code available in main.js. To run main.js, you have to do `npm install` within the repository. After doing that, you have to set the token. We also have to generate the ssh key using `ssh-keygen` and paste the RSA key in our DigitalOcean account.
##### Set your token

```
# Mac/Linux
export DOTOKEN="xxx"
# Windows
setx DOTOKEN xxx
```

![DO-Creation](/img/DO_creation.png)

Then, run the program by `node main.js`. This will create a Droplet with an id. We have to use that id to get the ip address. This ip address can be used to log in to the system. We just need to type `ssh root@ipaddress` to log in into the system.

![DO-SSH](/img/ssh_do.png)

The source code will be able to perform the following tasks:

1. List regions
2. List VM images
3. Create droplet
4. Get droplet IP
5. Ping IP
6. ssh into the system
7. Destroy droplet
8. Ping IP, make sure dead.

### Google Cloud

The source code of the Google Cloud is available in Python. We will be creating a VM instance in the compute engine of the Google Cloud using API reference.

You have to initially run `pip -r install requirements.txt` to complete all the required software and API. In Google Cloud, you have to start by authorizing yourself. To do that, you need to go to the service request page and create a reference for the project. It will create a JSON file. Copy that file into the location. This will contain some important information like email, ssh key, API token, etc. THIS FILE IS NOT INCLUDED IN THE REPOSITORY DUE TO SECURITY REASONS. 

#### Set up the authentication
```
export GOOGLE_APPLICATION_CREDENTIALS="[PATH]"
```

After doing that, you have to run the create_instance.py using two arguments. The first argument will be the project id which is available in the Project page of the Google Cloud instance and the second argument will be the bucket name. The location and system and are already set in the python file. If we want, we can set them too by passing them as an argument. The system runs by creating an instance and then displays an IP address. We can ping that IP address in a different window.

![GC-Creation](/img/GC_creation.png)

To ssh into the system, we can type the following gcloud command:

`gcloud compute --project "<project_name>" ssh --zone "<zone>" "<bucket_name>"`

When we press enter, it will delete the instance created(auto-triggered).

![GC-SSH](/img/ssh_gc.png)

The source code will be able to perform the following tasks:
1. Create instance.
2. Ping IP
3. ssh into the system
4. Destroy instance
5. Ping IP, make sure dead.

### Screencast
The screencast for this assignment is available [here](https://drive.google.com/file/d/1javmRfr2RRUiswgTne1z2sdlxj_ceXl8/view?usp=sharing).

### References
1. https://developers.digitalocean.com/v2/
2. https://github.com/CSC-DevOps/Course/blob/master/HW/HW1-A.md
3. https://cloud.google.com/compute/docs/
4. https://github.com/GoogleCloudPlatform/python-docs-samples
