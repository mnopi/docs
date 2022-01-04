# [gcloud](https://cloud.google.com/sdk/gcloud/reference)

[E2 versus N1](https://cloud.google.com/blog/products/compute/google-compute-engine-gets-new-e2-vm-machine-types)

## [Pricing: cheapest](https://cloud.google.com/compute/all-pricing?_ga=2.159239923.-818923441.1633936702)

Region: **us-central1** and **us-east1**

- e2-micro (2vCPU, 1 GB, 100 GB) **$10.11**
- e2-small (2 vCPUs, 2 GB, 100 GB) **$16.23**
- e2-medium (2 vCPUs, 4 GB, 100 GB) **$28.26**
- n1-standard-1 (1vCPU, 7.5 GB, 100 GB) **$28.27**

```bash
gcloud compute instances create docker \
    --machine-type=n1-standard-1 \
    --can-ip-forward \
    --tags=ubuntu,docker \
    --image-project=centos-cloud \
    --image-family=centos-7 \
    --boot-disk-size=50 \
    --boot-disk-type=pd-standard
```

### Share-core-machine: E2 shared-core machine types
- e2-micro (2 vCPUs 1 GB) **$6.11**
- e2-small (2 vCPUs 2 GB) **$12.23**
- e2-medium (2 vCPUs 4 GB) **$24.26**

**E2 shared-core custom machine types** are subject to the **same pricing rates as E2 custom machines**. 
These instances have fractional vCPUs with a custom memory range.


### Share-core-machine: N1 shared-core machine types
- f1-micro (0.2 vCPUs 0.60 GB) **$3.88**, (2 vCPUs 6 GB) **$33.88**
- g1-small (0.5 vCPUs 1.70 GB) **$13.13**

## N1 machine types
- n1-standard-1: -1 is the vCPUs (3.75 GB per vCPU). `n1-standard-2` **$24.27**
- n1-standard-*: -2 is the vCPUs (3.75 GB per vCPU). `n1-standard-2` **$48.54**
- custom vCPUs and memory: 1 vCPU **$16.95**, 1 GB **$2.27** (Total: **$19.22**)
- extend custom memory: 1 GB **$4.88**

## [Disk](https://cloud.google.com/compute/all-pricing?_ga=2.159239923.-818923441.1633936702#disk)
- Persistent standard provisioned space: **$0.040 per GB** (**100 GB: $4**)
- Persistent SSD provisioned space: **$0.170 per GB** (**100 GB: $17**)
- Persistent Snapshot storage: **$0.26 per GB** (**100 GB: $2.6**)
- Local SSD provisioned space: **$0.080 per GB** (**100 GB: $8**)
- Custom image storage: **$0.050 per GB** (**100 GB: $5**)
- Machine image: **$0.050 per GB** (**100 GB: $5**)

## [Network pricing](https://cloud.google.com/vpc/network-pricing)
- External IP: Static IP address (assigned but unused) **$7.20**
- External IP: Static and ephemeral IP addresses in use on standard VM instances **$2.80**
- External IP: Static and ephemeral IP addresses in use on preemptible VM instances **$1.44**
- External IP: Static and ephemeral IP addresses attached to forwarding rules, used by 
[Cloud NAT](https://cloud.google.com/nat/docs/overview), or used as a public IP for a Cloud VPN tunnel **Free**

```bash
gcloud compute addresses list
```

## GPU
**VERY Expensive !**, no `--enable-display-device`.

## Premium Images: Ubuntu Pro
**Expensive !**, pay for license cost per memory and license per vCPU.

## Suspended VM Instance 
- Instance memory and device state:  **$0.170 per GB** (**100 GB: $17**)

## PROJECT
````bash
export CLOUDSDK_CORE_PROJECT="jose-lumenbiomics"
cloud config set project "jose-lumenbiomics"
gcloud init
gcloud compute project-info describe
````
### Delete Project
```bash
open https://console.cloud.google.com/iam-admin/projects?_ga=2.146249012.1036757203.1633936702-818923441.1633936702
open https://cloud.google.com/compute/docs/instances/stopping-or-deleting-an-instance#delete_an_instance
open https://cloud.google.com/vpc/docs/using-firewalls#deleting_firewall_rules
```

### REGION/ZONE
````bash
gcloud compute regions list
gcloud compute zones list

````

#### Environment
````bash
export CLOUDSDK_COMPUTE_REGION="US-EAST1"
export CLOUDSDK_COMPUTE_ZONE="US-EAST1-B"
gcloud init
````

#### Command
````bash
gcloud config set compute/region us-east1
gcloud init
````
````bash
gcloud gcloud config set compute/zone us-east1-b
gcloud init
````

#### Metadata
`open https://console.cloud.google.com/compute/metadata?project=jose-lumenbiomics&supportedpurview=project` or:
````bash
gcloud --project "" compute project-info add-metadata \
  --metadata google-compute-default-region=us-east1,google-compute-default-zone=us-east1-b
gcloud init
````

## INSTANCES
````bash
gcloud compute instances create VM_NAME \
  [--image IMAGE | --image-family IMAGE_FAMILY] \
  --image-project IMAGE_PROJECT
gcloud compute instances list
gcloud compute instances describe VM_NAME
gcloud compute instances start VM_NAME
gcloud compute instances stop VM_NAME
gcloud compute instances add-labels VM_NAME \
  --label=KEY=VALUE
````

#### Reboot
````bash
gcloud compute instances reset example-instance --zone us-central1-a
````

## SSH
````bash
gcloud compute ssh VM_NAME
gcloud compute scp LOCAL_FILE_PATH VM_NAME:REMOTE_DIRECTORY
gcloud compute scp VM_NAME:REMOTE_DIRECTORY LOCAL_FILE_PATH
````

## SNAPSHOT
````bash
gcloud compute disks list
````

## SNAPSHOT
````bash
gcloud compute snapshots list
gcloud compute snapshots describe SNAPSHOT_NAME
gcloud compute snapshots delete SNAPSHOT_NAME
````

## FIREWALL
````bash
gcloud compute firewall-rules describe FIREWALL_RULE_NAME
````

## METADATA
````bash
gcloud compute project-info add-metadata VM_NAME \
  --metadata=KEY=VALUE,[KEY=VALUE]
gcloud compute instances add-metadata VM_NAME \
  --metadata=KEY=VALUE,[KEY=VALUE]
````

## OPTIONS
````bash
gcloud compute regions describe us-central1 --format json
gcloud compute instances list --filter="name ~ .*test.*"
gcloud compute operations list --filter="zone:(us-central1-a)" | grep DONE | grep 200
gcloud compute disks list --sort-by ~NAME --filter="zone:(us-central1-a)"
gcloud compute instances list --uri --filter="name~'^example-.*'"
gcloud compute instances delete $(gcloud compute instances list --uri --filter="name~'^example-.*'")
gcloud compute instances describe example-instance --zone asia-east1-b
gcloud compute instances describe example-instance --zone asia-east1-b --format text
gcloud compute operations list --filter="zone:(us-central1-a)"
gcloud compute operations describe example-instance --zone asia-east1-b
gcloud compute operations describe example-instance --zone asia-east1-b --format text
gcloud compute operations describe \
  operation-1406155165815-4fee4032850d9-7b78077c-a170c5c0 --zone us-central1-a
gcloud compute operations list --filter="zone:(us-central1-a)"
gcloud compute operations describe \
  operation-1406155165815-4fee4032850d9-7b78077c-a170c5c0 --zone us-central1-a
gcloud compute instances describe example-instance \
  --zone us-central1-a \
  --format json
gcloud auth list
gcloud auth revoke
````

## [SCRIPTING/SERVICES](https://cloud.google.com/sdk/docs/scripting-gcloud)
[Service Account Page](https://console.cloud.google.com/iam-admin/serviceaccounts?_ga=2.137296304.1036757203.1633936702-818923441.1633936702)
To create and download the associated private key as a JSON-formatted key file, 
choose Manage Keys from the action menu for the service account.
````bash
gcloud auth activate-service-account --key-file gcloud.json
````

### Disabling prompts
````bash
gcloud debug targets list --quiet
````

### Examples 
````bash
gcloud compute instances list --filter="zone:us-central1-a"
gcloud projects list --format="json" \
  --filter="labels.env=test AND labels.version=alpha"
gcloud projects list \
  --format="table(name, project_id, createTime.date(tz=LOCAL))"
gcloud projects list \
  --format="table(projectNumber,projectId,createTime)" \
  --filter="createTime.date('%Y-%m-%d', Z)='2016-05-11'"
gcloud compute regions describe us-central1 \
  --format="table(quotas:format='table(metric,limit,usage)')"
     gcloud compute project-info describe --flatten='quotas[]' \
    --format='csv(quotas.metric,quotas.limit,quotas.usage)'
        gcloud compute instances list \
    --format='table[box,title=Instances](name:sort=1,zone:label=zone,status)'
        
````

### Billing 
Enable Cloud build API
```bash
open https://console.cloud.google.com/marketplace/product/google/cloudbuild.googleapis.com?cloudshell=true&project=jose-lumenbiomics
open https://console.cloud.google.com/apis/credentials/consent?cloudshell=true&project=jose-lumenbiomics
```
### email
````bash
gcloud info --format='value(config.account)'
````

## [Create a Virtual Workstation](https://cloud.google.com/architecture/creating-a-virtual-linux-workstation?hl=en)
### Enable API
````bash
open https://console.cloud.google.com/flows/enableapi?apiid=compute_component&_ga=2.204847376.1036757203.1633936702-818923441.1633936702
````
### [Go to Cloud Shell](https://console.cloud.google.com/home/dashboard?cloudshell=true&_ga=2.207928722.1036757203.1633936702-818923441.1633936702&project=jose-lumenbiomics)
Create a graphic `n1-standard-4` with **4 vCPUs and 15 GB of RAM**,  
**50-GB standard persistent boot disk** and internet egress.
````bash
open https://console.cloud.google.com/home/dashboard?cloudshell=true&_ga=2.207928722.1036757203.1633936702-818923441.1633936702&project=jose-lumenbiomics
gcloud config set compute/zone us-west2-b
gcloud compute instances create test-vws \
    --machine-type=n1-standard-4 \
    --enable-display-device \
    --can-ip-forward \
    --tags=https-server \
    --image-project=centos-cloud \
    --image-family=centos-7 \
    --boot-disk-size=50 \
    --boot-disk-type=pd-standard
gcloud compute ssh test-vws
sudo passwd `whoami`
````

#### Graphics 
````bash
sudo yum -y update
sudo yum -y groupinstall 'Server with GUI'
````

#### Teradici Cloud Access Software
Teradici Cloud Access Software provides an agent that runs on your virtual workstation, 
delivering the desktop to your hardware or software client.

##### On VM
````bash
sudo yum -y install https://downloads.teradici.com/rhel/teradici-repo-latest.noarch.rpm
````
##### On Client
````bash
sudo yum -y update
sudo yum -y install pcoip-agent-standard
````

#### Register Teradici Agent 
````bash
pcoip-register-host --registration-code=registration-code
sudo reboot
gcloud compute firewall-rules create allow-teradici \
    --allow tcp:443,tcp:4172,udp:4172,tcp:60443
````

#### Signing to VM using PCo 
````bash
open https://docs.teradici.com/find/product/software-and-mobile-clients
````
- Select New Connection.
- In the Host Address field, enter the external IP address of your virtual workstation. 
If you want, you can enter a name for the connection.
- When you are connected, authenticate by entering the username and password 
that you created earlier for the virtual workstation.
- If you're prompted to select a desktop to run, select the one that you just created.
- Click Connect.

## [Create a Virtual Workstation](https://cloud.google.com/architecture/creating-a-virtual-workstation?hl=en)

## [automated-build-images-with-jenkins-kubernetes](https://cloud.google.com/architecture/automated-build-images-with-jenkins-kubernetes?hl=en)

## [Ubuntu]

## tests 
```bash
gcloud --project="jose-lumenbiomics" compute regions list
gcloud --project="jose-lumenbiomics" compute zones list
gcloud config set project "jose-lumenbiomics"
gcloud components update
gcloud config set compute/region us-east1
gcloud config set compute/zone us-east1-b
gcloud init

```
## TODO:
- Poner las variables de metadata en el servidor con la region, pero tengo que saber la zona.
- diferencia entre n1 y Share-core-machine: E2
- `gcloud compute instances create docker --can-ip-forward`
- `gcloud compute instances create docker --image-project=centos-cloud`
- `gcloud compute instances create docker --image-family=centos-7`
- ip y si es cloud NAT 
- firewall de todo o con ufw y usuario.
- estado del precio gastado.
- IP. 
- Instalar gcloud https://cloud.google.com/sdk/docs/install
- Instalar gsutil (no que va por https) https://cloud.google.com/storage/docs/gsutil_install
- Plug in pycharm 
