
# Summary of cloud services and respective open-source equivalent 


Edit this Sheet then convert to Markdown: https://docs.google.com/spreadsheets/d/1Ibo41Cs_XNdCFSqmNiXEQ16h-ZU6ATb6CZrMdKsLsZI

|  **** | **** | **Open-Source** | **GCP** | **AWS** | **...** |
| --- | --- | --- | --- | --- | --- |
|  **Compute** | IaaS |  | Compute Engine | Amazon Elastic Compute Cloud |  |
|   | PaaS |  |  |  |  |
|   | Containers |  | Google Kubernetes Engine | Amazon Elastic Container Service |  |
|   | Containers without infrastructure |  | Cloud Run | AWS Fargate |  |
|   | FaaS |  |  |  |  |
|   | Managed Batch Computing |  |  |  |  |
|  **Network** | Virtual Networks |  | Virtual Private Cloud | Amazon Virtual Private Cloud |  |
|   | Load Balancer |  | Cloud Load Balancing | Elastic Load Balancer |  |
|   | Dedicated Interconnect |  | Cloud Interconnect | Direct Connect |  |
|   | Domains and DNS |  | Google Domains, Cloud DNS | Amazon Route 53 |  |
|   | CDN |  | Cloud CDN | Amazon CloudFront |  |
|  **Storage** | Object Storage |  | Cloud Storage | Amazon Simple Storage Service |  |
|   | Block Storage |  |  |  |  |
|   | Reduced-availability Storage |  | Cloud Storage Nearline | Amazon S3 Standard-Infrequent Access, Amazon S3 One Zone-Infrequent Access |  |
|   | Archival Storage |  | Cloud Storage Coldline | Amazon Glacier |  |
|   | File Storage |  | Cloud Filestore (beta) | Amazon Elastic File System |  |
|  **Database** | RDBMS | MySQL | Cloud SQL, Cloud Spanner | Amazon Relational Database Service, Amazon Aurora |  |
|   | NoSQL: Key-value |  | [Cloud Firestore, Cloud Bigtable](https://cloud.google.com/firestore/ "Cloud Firestore, Cloud Bigtable") | Amazon DynamoDB |  |
|   | NoSQL: Indexed |  | Cloud Firestore | Amazon SimpleDB |  |
|  **Big Data & Analytics** | Batch Data Processing |  | Cloud Dataproc, Cloud Dataflow | Amazon Elastic MapReduce, AWS Batch |  |
|   | Stream Data Processing |  | Cloud Dataflow | Amazon Kinesis |  |
|   | Stream Data Ingest |  | Cloud Pub/Sub | Amazon Kinesis |  |
|   | Analytics |  | BigQuery | Amazon Redshift, Amazon Athena |  |
|   | Workflow Orchestration | Apache AirFlow | Cloud Composer | Amazon Data Pipeline, AWS Glue |  |
|  **Application Services** | Messaging | Apache Kafka | Cloud Pub/Sub | Amazon Simple Notification Service, Amazon Simple Queueing Service |  |
|  **Management Services** | Monitoring |  | Stackdriver Monitoring | Amazon CloudWatch |  |
|   | Logging |  | Stackdriver Logging | Amazon CloudWatch Logs |  |
|   | Deployment |  |  |  |  |
|  **Machine Learning** | Speech |  |  |  |  |
|   | Vision |  |  |  |  |
|   | Natural Language Processing |  |  |  |  |
|   | Translation |  |  |  |  |
|   | Conversational Interface |  |  |  |  |
|   | Video Intelligence |  |  |  |  |
|   | Auto-generated Models |  |  |  |  |
|   | Fully Managed ML |  |  |  |  |
|   |  |  |  |  |  |
|  **Infrastructure Deployment Tools** | infrastructure-as-code |  |  |  |  |
|  **Mobile** | Authentication |  |  |  |  |
|   | Database |  |  |  |  |
|   | Data Storage/CDN |  |  |  |  |
|   | Serverless routines |  |  |  |  |
|   | Notifications |  |  |  |  |
|   | Client application services |  |  |  |  |
## Resources/Articles

- [GCP vs AWS platforms](https://cloud.google.com/docs/compare/aws/#resource_management_interfaces)
- [Open-source Cloud tools](https://dzone.com/articles/top-5-enterprise-etl-tools)
- [Open-source tools matched with Cloud service providers](https://www.griddynamics.com/technologies/data-platform/cloud-native-data-platform)


# GCP Fundamentals: Core Infrastructure

## Content

* [What is Cloud Computing](#what-is-cloud-computing)
* [IaaS vs PaaS vs SaaS](#iaas-vs-paas-vs-saas)
* [GCP Multi-regions, Regions &amp; Zones](#gcp-multi-regions-regions--zones)
* [Pricing innovations](#pricing-innovations)
* [Multi-layered security approach](#multi-layered-security-approach)
* [Starting with Google Cloud](#starting-with-google-cloud)
    * [Projects](#projects)
    * [IAM](#iam)
* [GCP resource hierarchy](#gcp-resource-hierarchy)
* [Identity and Access Management (IAM)](#identity-and-access-management-iam)
    * [Who (Account/Identity)/Doing what (Roles)/On which resources?](#who-accountidentitydoing-what-roleson-which-resources)
    * [Services Accounts](#services-accounts)
* [Interacting with GCP](#interacting-with-gcp)
    * [Cloud Marketplace (formerly Cloud Launcher)](#cloud-marketplace-formerly-cloud-launcher)
* [Virtual Machines on GCP](#virtual-machines-on-gcp)
    * [Virtual Private Cloud (VPC) Network](#virtual-private-cloud-vpc-network)
    * [Compute Engine](#compute-engine)
    * [Important VPC capabilities](#important-vpc-capabilities)
    * [Create a VM from Console](#create-a-vm-from-console)
    * [Create a VM with gcloud in Cloud Shell](#create-a-vm-with-gcloud-in-cloud-shell)
    * [Lab about Compute Engine](#lab-about-compute-engine)
* [GCP Storage Options](#gcp-storage-options)
    * [Cloud Storage &amp; Cloud Storage interactions](#cloud-storage--cloud-storage-interactions)
    * [Google Cloud Bigtable](#google-cloud-bigtable)
    * [Google Cloud Datastore](#google-cloud-datastore)
    * [Google Cloud SQL](#google-cloud-sql)
    * [Google Cloud Spanner](#google-cloud-spanner)
    * [Lab: Cloud Storage / Cloud SQL](#lab-cloud-storage--cloud-sql)
* [Containers, Kubernetes, and Kubernetes Engine](#containers-kubernetes-and-kubernetes-engine)
    * [Containers](#containers)
    * [Kubernetes](#kubernetes)
    * [Lab: Containers / Kubernetes / GKE](#lab-containers--kubernetes--gke)
* [App Engine](#app-engine)
    * [<strong>Standard</strong> Environment](#standard-environment)
    * [<strong>Flexible</strong> Environment](#flexible-environment)
    * [Comparison Standard vs Flexible](#comparison-standard-vs-flexible)
    * [Comparison App Engine vs Kubernetes Engine](#comparison-app-engine-vs-kubernetes-engine)
* [Google Cloud Endpoints and Apigee Edge](#google-cloud-endpoints-and-apigee-edge)
    * [Lab: Getting Started with App Engine](#lab-getting-started-with-app-engine)
* [Development in the cloud](#development-in-the-cloud)
* [Deployment: Infrastructure as code](#deployment-infrastructure-as-code)
* [Monitoring: Proactive instrumentation (Stackdriver &amp; )](#monitoring-proactive-instrumentation-stackdriver--)
    * [lab: Getting Started with Deployment Manager and Stackdriver](#lab-getting-started-with-deployment-manager-and-stackdriver)
* [Big Data and Machine Learning](#big-data-and-machine-learning)
    * [Dataproc](#dataproc)
    * [Dataflow](#dataflow)
    * [BigQuery](#bigquery)
    * [Cloud Pub/Sub and Cloud Datalab](#cloud-pubsub-and-cloud-datalab)
    * [Google Cloud Machine Learning Platform](#google-cloud-machine-learning-platform)
    * [Machine learning APIs](#machine-learning-apis)
    * [lab: Getting Started with BigQuery](#lab-getting-started-with-bigquery)
* [Summary](#summary)
* [Resources/Articles](#resourcesarticles)



## What is Cloud Computing

The US National Institute of Standards and Technology created a definition
It has 5 equally important traits:

1. **computing resources on-demand and self-service**. All you have to do is use a simple interface and you get the processing power, storage, and network you need, with no need for human intervention. 
1. **access these resources over the net from anywhere you want**. The provider of those resources has a big pool of them and allocates them to customers out of that pool. That allows the provider to get economies of scale by buying in bulk and pass the savings on to the customers. Customers don't have to know or care about the exact physical location of those resources.
1. **the resources are elastic**. If you need more resources you can get more, rapidly. If you need less, you can scale back.
1. the **customers pay only for what they use** or reserve as they go. If they stop using resources, they stop paying.

## IaaS vs PaaS vs SaaS

Virtualized data centers brought you Infrastructure as a Service, IaaS, and Platform as a Service, PaaS offerings.

- IaaS offerings provide raw compute, storage, and network organized in ways that are familiar from data centers.
- PaaS offerings, on the other hand, bind application code you write to libraries that give access to the infrastructure your application needs. That way, you can just focus on your application logic.

In the IaaS model, you pay for what you allocate.

In the PaaS model, you pay for what you use.

Both sure beat the old way where you bought everything in advance based on lots of risky forecasting. As Cloud Computing has evolved, the momentum has shifted towards managed infrastructure and managed services. GCP offers many services in which you need not worry about any resource provisioning at all. We'll discuss many in this course. They're easy to build into your applications and you pay per use.

What about SaaS? Of course, Google's popular applications like, Google Search, Gmail, Google Docs and Google Drive are Software as a Service applications in that they're consumed directly over the internet by end users (e.g. GSuite).

<img src="../images/GCP_IaaS_PaaS_FaaS.png"
     alt="GCP_IaaS_PaaS_FaaS.png"
     style="float: left; margin-right: 10px;" />

article: https://cloud.google.com/blog/products/gcp/time-to-hello-world-vms-vs-containers-vs-paas-vs-faas

## GCP Multi-regions, Regions & Zones

<img src="../images/GCP_regions_zones.png"
     alt="GCP_regions_zones.png"
     style="float: left; margin-right: 10px;" />

- in several zones of the same regions **for fault tolerance**,
- in several regions around the world **for better performance**.


## Pricing innovations

- **Per second billing**: Google was the first major Cloud provider to bill by the second rather than rounding up to bigger units of time for its virtual machines as a service offering.  This may not sound like a big deal, but charges for rounding can really add up for customers who are creating and running lots of virtual machines. 
Per second billing is offered for a virtual machine use through Compute Engine and for several other services too which we'll also look at in this course. Kubernetes engine which is Container Infrastructure as a Service, Cloud Dataproc which is the open source big data system Hadoop as a Service, and App Engine's Flexible Environment, which is a Platform as a Service.
- **Discounts for sustained use**: Compute Engine offers automatically applied sustained use discounts which are automatic discounts that you get for running a virtual machine for a significant portion of the billing month. When you run an instance for more than 25 percent of a month, Compute Engine automatically gives you a discount for every incremental minute you use it. Here's one more way Compute Engine saves money. Later in this course, you'll learn about how virtual machines are configured. Among other things, you specify how much memory and how many virtual CPUs they should have. 
- **Custom virtual machine types**: Normally, you pick a virtual machine type from a standard set of these values, but Compute Engine also offers custom virtual machine types, so that you can fine-tune the sizes of the virtual machines you use. That way, you can tailor your pricing for your workloads.

## Multi-layered security approach

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/2K73n/multi-layered-security-approach)

<img src="../images/GCP_security.png"
     alt="GCP_regions_zones.png"
     style="float: left; margin-right: 10px;" />

## Starting with Google Cloud

your **workloads in GCP**:
- you use **projects** to organize them.
- You use **Google Cloud Identity**, and **Access Management**, also called IM, or IAM to control who can do what.
- you use your choice of several interfaces to connect.


### Projects

Projects are the main way you organize the resources you use in GCP. Use them to group together related resources, usually because they have a common business objective.

### IAM

The principle of least privilege is very important in managing any kind of compute infrastructure, whether it's in the Cloud or on-premises. This principle says that each user should have only those privileges needed to do their jobs. In a least-privilege environment, people are protected from an entire class of errors.
GCP customers use IM to implement least privilege, and it makes everybody happier. There are four ways to interact with GCP's management layer:
- through the **web-based console**,
- through the **SDK** and its command-line tools,
- through the **APIs**,
- and through a **mobile app**.

<img src="../images/Google_Security.png"
     alt="Google_Security.png"
     style="float: left; margin-right: 10px;" />


When you build an application on your on-premises infrastructure, you're responsible for the entire stack security. From the physical security of the hardware, and the premises in which they're housed, through the encryption of the data on disk, the integrity of your network, all the way up to securing the content stored in those applications. When you move an application to Google Cloud Platform, Google handles many of the lower layers of security. Because of its scale, Google can deliver a higher level of security at these layers than most of its customers could afford to do on their own. The upper layers of the security stack remain the customers' responsibility. Google provides tools such as IAM to help customers implement the policies they choose at these layers.

## GCP resource hierarchy

[video #1](https://www.coursera.org/learn/gcp-fundamentals/lecture/K85Wf/the-google-cloud-platform-resource-hierarchy)

[video #2](https://www.coursera.org/learn/gcp-fundamentals/lecture/K85Wf/the-google-cloud-platform-resource-hierarchy)

<img src="../images/GCP_organization_heirarchy.png"
     alt="GCP_organization_heirarchy.png"
     style="float: left; margin-right: 10px;" />

<table >
	<tbody>
		<tr>
			<td><img src="../images/GCP_resource_hierarchy.png"
                    alt="GCP_resource_hierarchy.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/Projects_in_a_Folder.png"
                    alt="Projects_in_a_Folder.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>


     

Policies are inherated downwards in the hierarchy.
<img src="../images/GCP_project_identifiers.png"
     alt="GCP_project_identifiers.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Example_without_folders.png"
     alt="Example_without_folders.png   "
     style="float: left; margin-right: 10px;" />

## Identity and Access Management (IAM)

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/1zsAc/identity-and-access-management-iam)

### Who (Account/Identity)/Doing what (Roles)/On which resources?

IAM lets administrators authorize who can take action on specific resources. An IAM policy has:
- a **"who" part**: The "who" part names the user or users you're talking about. The "who" part of an IAM policy can be defined either by:
  - a Google account,
  - a Google group,
  - a Service account,
  - an entire G Suite, 
  - or a Cloud Identity domain. 
- a **"can do what" part**: The "can do what" part is defined by an IAM role. An IAM role is a collection of permissions. Most of the time, to do any meaningful operations, you need more than one permission. For example, to manage instances in a project, you need to create, delete, start, stop, and change an instance. So the permissions are **grouped together into a role** that makes them easier to manage. 
- and an **"on which resource" part**: 

<img src="../images/roles_in_IAM.png"
     alt="roles_in_IAM.png"
     style="float: left; margin-right: 10px;" />
**3 kinds of roles in Cloud IAM**

- **Primitive roles** are broad. You apply them to a GCP project and they affect all resources in that project. These are the **owner**, **editor**, and **viewer roles**. If you're **a viewer on a given resource**, you can examine it but not change its state. If you're **an editor**, you can do everything a viewer can do, plus change its state. And if you are an owner, you can do everything an editor can do, plus manage rolls and permissions on the resource.
- **The owner role** on a project also lets you do one more thing: set up billing. - - Often, companies want someone to be able to control the billing for a project without the right to change the resources in the project. And that's why you can grant someone the **billing administrator role**.

**Predefined roles**
Be careful, if you have several people working together on a project that contains sensitive data, primitive roles are probably too coarse. 
Fortunately, GCP IAM provides a finer grained types of roles. GCP services offer their own sets of predefined roles and they define where those roles can be applied. For example, later in this course, we'll talk about Compute Engine, which offers virtual machines as a service. Compute Engine offers a set of predefined roles, and you can apply them to Compute Engine resources in a given project, a given folder, or in an entire organization. Another example. Consider Cloud Bigtable, which is a managed database service. Cloud Bigtable offers roles that can apply across an entire organization to a particular project or even to individual Bigtable database instances.

***IAM more fine-grained predefined roles** on particular services ([video](https://www.coursera.org/learn/gcp-fundamentals/lecture/CiocS/iam-roles)).

> A lot of companies have a least-privileged model in which each person in your organization has the minimum amount of privilege needed to do his or her job.

### Services Accounts

[mid of video](https://www.coursera.org/learn/gcp-fundamentals/lecture/CiocS/iam-roles)

What if you want to give permissions to a Compute Engine virtual machine, rather than to a person? Then you would use a service account.

<img src="../images/service_accounts.png"
     alt="service_accounts.png"
     style="float: left; margin-right: 10px;" />


## Interacting with GCP

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/hIpvL/interacting-with-google-cloud-platform)

<img src="../images/GCP_4_ways_interactions.png"
     alt="GCP_4_ways_interactions.png"
     style="float: left; margin-right: 10px;" />

[APIs Explorer](https://developers.google.com/apis-explorer)

### Cloud Marketplace (formerly Cloud Launcher)

[console.cloud.google.com/marketplace](https://console.cloud.google.com/marketplace)

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/AztZe/cloud-marketplace-formerly-cloud-launcher) 

A Quick way to get access to "solutions" with minimum effort.

e.g.:
- deploying a LAMP stack on GCP (LAMP stands for Linux, Apache, MySQL, PHP) > [video demo](https://www.coursera.org/learn/gcp-fundamentals/lecture/b8wYV/demonstration-getting-started-with-cloud-launcher).





## Virtual Machines on GCP

**Compute Engine** lets you run virtual machines on Google's global infrastructure.

### Virtual Private Cloud (VPC) Network

Your VPC networks connect your GCP resources to each other and to the internet:
- you can segment your networks,
- you can use firewall rules to restrict access to instances, and
- you can create static routes to forward traffic to specific destinations.

The way a lot of people get started with GCP is:

- to define their own Virtual Private Cloud inside their first GCP project,
- or they can simply choose the default VPC and get started with that.

<img src="../images/VPC_regions_subnets.png"
     alt="VPC_regions_subnets.png"
     style="float: left; margin-right: 10px;" />

 The Virtual Private Cloud networks that you define have **global scope**.
 
 > They can have subnets in any GCP region worldwide and **subnets can span the zones that make up a region**.
 > "In Google Cloud VPCs, subnets have regional scope."

 This architecture makes it easy for you to define your own network layout with global scope:
 - You can also have resources in different zones on the same subnet.
 - You can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it. Doing that doesn't affect already configured VMs. In this example, your VPC has one network. So far, it has one subnet defined in GCP `us-east1` region. Notice that it has two Compute Engine VMs attached to it. They're neighbors on the same subnet even though they are in different zones. You can use this capability to build solutions that are resilient but still have simple network layouts.

### Compute Engine

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/tv56B/compute-engine)

- OS, type of disk storage, software pre-installed with startup scripts, ...
- snapshots of disks
- preemptible VMs for jobs that can be stopped and restarted.

### Important VPC capabilities

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/wyDK3/important-vpc-capabilities)

- provided **router**
- provided **Firewall instances** to control traffic going through
- **VPC Peering** to interconnect outside your project 2 VPCs on GCP. And **Shared VPC** would provide the IAM functionalities to specify Who can access What.
- **Cloud Load Balancing**: Google Cloud Load Balancing allows you to balance HTTP-based traffic across multiple Compute Engine regions.

<img src="../images/Cloud_Load_balancing.png"
     alt="Cloud_Load_balancing.png"
     style="float: left; margin-right: 10px;" />

- **Cloud DNS**: programmable with REST API
- **Cloud CDN**: CDN stands for Content Delivery Network, a global system of **ddge caches** to cache content close to your users: better user-experience, less requests. Just enable it with checkbox!

### Create a VM from Console 

### Create a VM with gcloud in Cloud Shell

Create the new VM in the same region, but in another zone, setting `us-central1-c` as the new default zone:
<img src="../images/VM_gcloud.png"
     alt="VM_gcloud.png"
     style="float: left; margin-right: 10px;" />

SSH the new VM:
<img src="../images/VM_ping_ssh.png"
     alt="VM_ping_ssh.png"
     style="float: left; margin-right: 10px;" />


Install a simple webserver and edit its homepage on the new VM:
<img src="../images/VM_install_simple_webserver.png"
     alt="VM_install_simple_webserver.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/VM_edit_webserver_homepage.png"
     alt="VM_edit_webserver_homepage.png"
     style="float: left; margin-right: 10px;" />


Check that the running webserver serves the homepage locally on the new VM:

<img src="../images/VM_check_webser_serves_local_homepage.png"
     alt="VM_check_webser_serves_local_homepage.png"
     style="float: left; margin-right: 10px;" />

Check that the running webserver serves the homepage from the other VM on the same VPC:

<img src="../images/VM1_seeing_homepage_of_VM2.png"
     alt="VM1_seeing_homepage_of_VM2.png"
     style="float: left; margin-right: 10px;" />


### Lab about Compute Engine

[notes](../labs/lab_create_VMs_with_Compute_Engine.md) 




## GCP Storage Options

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/18wEV/introduction-to-google-cloud-platform-storage-options)

<img src="../images/Storage_COMPARISON.png"
     alt="Storage_COMPARISON.png"
     style="float: left; margin-right: 10px;" />

GCP has other storage options to meet your needs for:

- structured,
- unstructured,
- transactional
- and relational data.

Its core storage options:

- Cloud Storage
- Google Big Table (NoSQL)
- Cloud SQL, (RDBMS)
- Cloud Spanner (RDBMS),
- Cloud Data Store,


### Cloud Storage & Cloud Storage interactions

- [video 1](https://www.coursera.org/learn/gcp-fundamentals/lecture/HLKXf/cloud-storage)
- [video 2](https://www.coursera.org/learn/gcp-fundamentals/lecture/2uNqj/cloud-storage-interactions)

Cloud Storage objects are immutable

4 classes:

- "multi-regional" & "regional" are high-performance object classes
- "nearline" & "coldline" are backup/archivable storage

<img src="../images/Cloud_Storage_interactions_4classes.png"
     alt="Cloud_Storage_interactions_4classes.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Storage_CloudStorage_bring_data_in.png"
     alt="Storage_CloudStorage_bring_data_in.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Storage_CloudStorage_interactions_with_other_GCP_services.png"
     alt="Storage_CloudStorage_interactions_with_other_GCP_services.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Storage_CloudStorage_buckets.png"
     alt="Storage_CloudStorage_buckets.png"
     style="float: left; margin-right: 10px;" />

### Google Cloud Bigtable

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/8LIth/google-cloud-bigtable)

Definition: Google CLoud (fully-managed) NoSQL, BigData, database service for TeraBytes applications (up to PetaBytes of data).

<img src="../images/Storage_BigTable_interactions.png"
     alt="Storage_BigTable_interactions.png"
     style="float: left; margin-right: 10px;" />

### Google Cloud Datastore

[vidoe](https://www.coursera.org/learn/gcp-fundamentals/lecture/7sYyx/google-cloud-datastore)

Definition: Google CLoud Datastore is a managed horizontally scalable NoSQL database.


### Google Cloud SQL

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/fVTwB/google-cloud-sql-and-google-cloud-spanner)

a managed Relational Database Management System (RDBMS) database service. Either based on MySQL or PostgreSQLBeta.

It manages "database transactions".

### Google Cloud Spanner

[video, together with Cloud SQL](https://www.coursera.org/learn/gcp-fundamentals/lecture/fVTwB/google-cloud-sql-and-google-cloud-spanner)

Definition: Google Spanner is horizontally scalable Relational Database Management System (RDBMS).

### Lab: Cloud Storage / Cloud SQL

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/yboF1/demonstration-getting-started-with-cloud-storage-and-cloud-sql)

[notes](../labs/lab_create_blog_with_Cloud_Storage_Cloud_SQL_and_Compute_Engine.md) 

## Containers, Kubernetes, and Kubernetes Engine

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/XMTBL/containers-kubernetes-and-kubernetes-engine)


### Containers

<img src="../images/containers_IaaS.png"
     alt="containers_IaaS.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/containers_containers.png"
     alt="containers_containers.png"
     style="float: left; margin-right: 10px;" />

It scales like PaaS, but gives you nearly the same flexibility as IaaS.

With this abstraction, your code is ultra portable, and you can treat the OS and the hardware as a blackbox. You can go from your laptop to the cloud without changing or rebuilding anything.

<table >
		<tr>
			<td><img src="../images/containers_python_app.png"
                    alt="containers_python_app.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_python_requirements.png"
                    alt="containers_python_requirements.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_dockerfile.png"
                    alt="containers_dockerfile.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
		<tr>
			<td><img src="../images/containers_build_run_container.png"
                    alt="containers_build_run_container.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
</table>


### Kubernetes

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/XMTBL/containers-kubernetes-and-kubernetes-engine)

Let's you orchestrate many containers on many hosts, scale them as microsrvices and deploy rollouts and rollbacks.

Kubernetes is a set of APIs that you can use to deploy containers on a set of nodes called a cluster

GKE is "hosted Kubernetes" by Google!!

GKE clusters:

- can be customised,
- can be deloyed in one gcloud command: `gcloud container clusters create k1`
- check status in the Admin Console
- Then, you deploy containers on nodes using a wrapper around one or more containers called a pod. A Pod is the smallest unit in Kubernetes that you create or deploy

<table >
		<tr>
			<td><img src="../images/containers_k8s_cluster.png"
                    alt="containers_k8s_cluster.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_configure_with_GKE.png"
                    alt="containers_k8s_configure_with_GKE.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_POD_containers.png"
                    alt="containers_k8s_POD_containers.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
</table>

One way to run a container in a POD in Kubernetes is to use `kubectl`:

<table >
		<tr>
			<td><img src="../images/containers_k8s_kubectl.png"
                    alt="containers_k8s_kubectl.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_kubectl_networking.png"
                    alt="containers_k8s_kubectl_networking.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_kubectl_simple_loadbalancer.png"
                    alt="containers_k8s_kubectl_simple_loadbalancer.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
</table>

To get the IP of the load balancer:

<img src="../images/containers_k8s_kubectl_get_IPs.png"
                    alt="containers_k8s_kubectl_get_IPs.png"
                    style="float: left; margin-right: 10px;" />

To scale the deployment:

<table >
		<tr>
			<td><img src="../images/containers_k8s_kubectl_scale_deployment.png"
                    alt="containers_k8s_kubectl_scale_deployment.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_kubectl_autoscale_deployment.png"
                    alt="containers_k8s_kubectl_autoscale_deployment.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
</table>


the real strength of Kubernetes comes when you **work in a declarative way**. Instead of issuing commands, you provide a **configuration file** that tells Kubernetes what you want your desired state to look like, and Kubernetes figures out how to do it.

<table >
		<tr>
			<td><img src="../images/containers_k8s_kubectl_configuration_file.png"
                    alt="containers_k8s_kubectl_configuration_file.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_kubectl_configuration_file_app_nginx.png"
                    alt="containers_k8s_kubectl_configuration_file_app_nginx.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_kubectl_configuration_file_app_nginx_scale_3_to_5.png"
                    alt="containers_k8s_kubectl_configuration_file_app_nginx_scale_3_to_5.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/containers_k8s_kubectl_run_configuration_file.png"
                    alt="containers_k8s_kubectl_run_configuration_file.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
</table>

Watch the PODs come online:

<img src="../images/containers_k8s_kubectl_watch_PODs_come_onine.png"
                    alt="containers_k8s_kubectl_watch_PODs_come_onine.png"
                    style="float: left; margin-right: 10px;" />

Which ones are deployed?

<img src="../images/containers_k8s_kubectl_watch_PODs_deployed.png"
                    alt="containers_k8s_kubectl_watch_PODs_deployed.png"
                    style="float: left; margin-right: 10px;" />

Find out the external IP of the service(s):

<img src="../images/containers_k8s_kubectl_watch_PODs_get_IPs.png"
                    alt="containers_k8s_kubectl_watch_PODs_get_IPs.png"
                    style="float: left; margin-right: 10px;" />

And hit a public IP from a client:

<img src="../images/containers_k8s_kubectl_watch_PODs_hit_IPs_from_client.png"
                    alt="containers_k8s_kubectl_watch_PODs_hit_IPs_from_client.png"
                    style="float: left; margin-right: 10px;" />

What happens when you want to upload a new version of your app?

It might be too risky to **rollout** all of your services all at once!

Use `kubectl rollout ...` or change your **deployment configuration file** and apply the changes using `kubectl apply`:

New PODs will get created according to your update strategy:

> Here's an example configuration that will create a new version of your pods one-by-one, and wait for a new pod to be available before destroying one of the old pods.

<img src="../images/containers_k8s_kubectl_update_code_rollout.png"
                    alt="containers_k8s_kubectl_update_code_rollout.png"
                    style="float: left; margin-right: 10px;" />

### Lab: Containers / Kubernetes / GKE

[video: k8s on GKE is much more...](https://www.coursera.org/learn/gcp-fundamentals/lecture/1aWl8/demo-and-lab-introduction)

> _There are a lot of features in Kubernetes and GKE we haven't even touched on, such as configuring health checks, setting session affinity, managing different rollout strategies, and deploying pods across regions for high availability. But for now, that's enough. In this module, you've learned how to build a run containerized applications, orchestrate and scale them on a cluster, and deploy them using rollouts. Now you'll see how to do it in a demo and practice it in a lab exercise._

- [video: lab](https://www.coursera.org/learn/gcp-fundamentals/lecture/umRjO/demo-getting-started-with-kubernetes-engine)
- [notes lab](../labs/lab_create_a_webserver_deployed_on_kubernetes_cluster.md) 


## App Engine

- [video #1](https://www.coursera.org/learn/gcp-fundamentals/lecture/PrttY/google-app-engine-standard-environment)
- [video #2](https://www.coursera.org/learn/gcp-fundamentals/lecture/4ZurT/google-app-engine-flexible-environment)


- Compute infrastructure (IaaS): **Compute Engine** & **Kubernetes Engine**
- Platform-as-a-Service (PaaS) and "focus on your code": **App Engine**

App Engine:

- scales automatically
- you pay for what you use
- 2 environments: **Standard** & **Flexible**

### **Standard** Environment

- Simpler type: works in sandbox (why it can scales)
- Some environment at NO charge
- has contraints: "60 seconds time-out" (if not suitable, move to Flexible)
- Runtime for Java, Python, PHP and Go


<img src="../images/AppEngine_Standard_example_workflow.png"
        alt="AppEngine_Standard_example_workflow.png"
        style="float: left; margin-right: 10px;" />

### **Flexible** Environment

- runs on containers (running on VMs)
- Allows to configure your containers
- Use standard runtime


### Comparison Standard vs Flexible

<img src="../images/AppEngine_Comparison_standard_flexible.png"
        alt="AppEngine_Comparison_standard_flexible.png"
        style="float: left; margin-right: 10px;" />

### Comparison App Engine vs Kubernetes Engine

<img src="../images/AppEngine_Comparison_app_engine_vs_Kubernetes_engine.png"
        alt="AppEngine_Comparison_app_engine_vs_Kubernetes_engine.png"
        style="float: left; margin-right: 10px;" />


## Google Cloud Endpoints and Apigee Edge

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/tPtB0/google-cloud-endpoints-and-apigee-edge)

- What's an API? a clean, well-defined interface that abstract away needless details on the service's implementation

Google provides 2 APIs-related approach:

- **Cloud Endpoints**: managed API proxies
- **Apigee Edge**: also a managed API proxies, but business-oriented (rate limiting, quotas, analytics), providing a software service to OTHER companies.

<table >
	<tbody>
		<tr>
			<td><img src="../images/API_Cloud_Endpoints.png"
                    alt="API_Cloud_Endpoints.png"
                    style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/API_Cloud_Endpoints_managed_Proxy.png"
                    alt="API_Cloud_Endpoints_managed_Proxy.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
		<tr>
			<td><img src="../images/API_Cloud_Endpoints_supported_platforms.png"
                    alt="API_Cloud_Endpoints_supported_platforms.png"
                    style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>


<img src="../images/API_ApigeeEdge.png"
                    alt="API_ApigeeEdge.png"
                    style="float: left; margin-right: 10px;" />


Many users of Apigee Edge are providing a software service to other companies and those features come in handy.

> Because of the backend services for Apigee Edge need not be in GCP, engineers often use it when they are "taking apart" a legacy application. Instead of replacing a monolithic application in one risky move, they can instead use Apigee Edge to peel off its services one by one, standing up microservices to implement each in turn, until the legacy application can be finally retired.

### Lab: Getting Started with App Engine

- [video](https://www.coursera.org/learn/gcp-fundamentals/lecture/T1C9J/demonstration-getting-started-with-app-engine)
- [notes lab](../labs/lab_deploy_appengine_webapp.md)


## Development in the cloud

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/8Hfmz/development-in-the-cloud)

- Git: hosted git (private) provider > **Cloud Source Repositories**
- Managed applications which can be triggered (events in Cloud Storage, in Cloud Pub/Sub or an HTTP call): **Cloud Functions (beta)**


## Deployment: Infrastructure as code

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/0hYEJ/deployment-infrastructure-as-code)

It's often more efficient to **use a template** to set up your GCP environment.

That means a specification of what the environment should look like. It's **declarative** rather than **imperative**, using either:
- `yaml` markup language
- or `Python`

Then you give the template to [**Deployment Manager**](https://cloud.google.com/deployment-manager/docs/), and you allows you to version control your deployment templates in Git repositories (e.g. Cloud Source Repositories).

## Monitoring: Proactive instrumentation (Stackdriver & )

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/cHNEH/monitoring-proactive-instrumentation)

You can't run an application stably without monitoring. Monitoring lets you figure out whether the changes you made were good or bad. It lets you respond with information rather than with panic, when one of your end users complains that your application is down

Stackdriver is GCP's tool for monitoring, logging and diagnostics.

<img src="../images/Monitoring_StackDriver.png"
        alt="Monitoring_StackDriver.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Monitoring_StackDriver_services.png"
        alt="Monitoring_StackDriver_services.png"
        style="float: left; margin-right: 10px;" />

### lab: Getting Started with Deployment Manager and Stackdriver

- [video lab](https://www.coursera.org/learn/gcp-fundamentals/lecture/CJO1F/demonstration-getting-started-with-deployment-manager-and-stackdriver)
- notes lab 



## Big Data and Machine Learning

- [video #1](https://www.coursera.org/learn/gcp-fundamentals/lecture/6WqVr/introduction-to-big-data-and-machine-learning)
- [video #2](https://www.coursera.org/learn/gcp-fundamentals/lecture/gP7vk/google-cloud-big-data-platform)
- [video #3](https://www.coursera.org/learn/gcp-fundamentals/lecture/OK31U/cloud-dataflow)
- [video #4](https://www.coursera.org/learn/gcp-fundamentals/lecture/KM2ei/bigquery)
- [video #5](https://www.coursera.org/learn/gcp-fundamentals/lecture/LnOme/cloud-pub-sub-and-cloud-datalab)
- [video #6](https://www.coursera.org/learn/gcp-fundamentals/lecture/x2zsd/google-cloud-machine-learning-platform)
- [video #7](https://www.coursera.org/learn/gcp-fundamentals/lecture/VwUfz/machine-learning-apis)

<img src="../images/BigData_ML_tools.png"
        alt="BigData_ML_tools.png"
        style="float: left; margin-right: 10px;" />

### Dataproc

- [video #2](https://www.coursera.org/learn/gcp-fundamentals/lecture/gP7vk/google-cloud-big-data-platform)

<img src="../images/BigData_ML_Dataproc.png"
        alt="BigData_ML_Dataproc.png"
        style="float: left; margin-right: 10px;" />


- Spark/SparkSQL for data mining
- MLlib (Spark ML libraries)

### Dataflow

- [video #3](https://www.coursera.org/learn/gcp-fundamentals/lecture/OK31U/cloud-dataflow)

<table >
	<tbody>
		<tr>
			<td><img src="../images/BigData_ML_Dataflow.png"
        alt="BigData_ML_Dataflow.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_Dataflow_pipelines.png"
        alt="BigData_ML_Dataflow_pipelines.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_Dataflow_ETL_tool.png"
        alt="BigData_ML_Dataflow_ETL_tool.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_Dataflow_orchestration.png"
        alt="BigData_ML_Dataflow_orchestration.png"
        style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>

<img src="../images/BigData_ML_Dataflow_pipeline_example.png"
        alt="BigData_ML_Dataflow_pipeline_example.png"
        style="float: left; margin-right: 10px;" />


### BigQuery

- [video #4](https://www.coursera.org/learn/gcp-fundamentals/lecture/KM2ei/bigquery)

<table >
	<tbody>
		<tr>
			<td><img src="../images/BigData_ML_BigQuery.png"
        alt="BigData_ML_BigQuery.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_BigQuery_fully_managed.png"
        alt="BigData_ML_BigQuery_fully_managed.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_BigQuery_global_service.png"
        alt="BigData_ML_BigQuery_global_service.png"
        style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>


### Cloud Pub/Sub and Cloud Datalab

- [video #5](https://www.coursera.org/learn/gcp-fundamentals/lecture/LnOme/cloud-pub-sub-and-cloud-datalab)

<table >
	<tbody>
		<tr>
			<td><img src="../images/BigData_ML_PubSub.png"
        alt="BigData_ML_PubSub.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_PubSub_usage.png"
        alt="BigData_ML_PubSub_usage.png"
        style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>


<table >
	<tbody>
		<tr>
			<td><img src="../images/BigData_ML_Datalab.png"
        alt="BigData_ML_Datalab.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_Datalab_interactions.png"
        alt="BigData_ML_Datalab_interactions.png"
        style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>

 
### Google Cloud Machine Learning Platform

- [video #6](https://www.coursera.org/learn/gcp-fundamentals/lecture/x2zsd/google-cloud-machine-learning-platform)

<img src="../images/BigData_ML_ML_platform.png"
        alt="BigData_ML_ML_platform.png"
        style="float: left; margin-right: 10px;" />


### Machine learning APIs

- [video #7](https://www.coursera.org/learn/gcp-fundamentals/lecture/VwUfz/machine-learning-apis)

<table >
	<tbody>
		<tr>
			<td><img src="../images/BigData_ML_API_Vision.png"
        alt="BigData_ML_API_Vision.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_API_Vision_aplications.png"
        alt="BigData_ML_API_Vision_aplications.png"
        style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>


<table >
	<tbody>
		<tr>
			<td><img src="../images/BigData_ML_API_Natural_Language.png"
        alt="BigData_ML_API_Natural_Language.png"
        style="float: left; margin-right: 10px;" />
            </td>
			<td><img src="../images/BigData_ML_API_Natural_Language_applications.png"
        alt="BigData_ML_API_Natural_Language_applications.png"
        style="float: left; margin-right: 10px;" />
            </td>
		</tr>
	</tbody>
</table>


<img src="../images/BigData_ML_API_Translation.png"
        alt="BigData_ML_API_Translation.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/BigData_ML_API_VideoBeta.png"
        alt="BigData_ML_API_VideoBeta.png"
        style="float: left; margin-right: 10px;" />

### lab: Getting Started with BigQuery

- [video lab](https://www.coursera.org/learn/gcp-fundamentals/lecture/V6Daj/demonstration-getting-started-with-bigquery)
- [notes lab](../labs/lab_load_data_and_query_BigQuery.md)


## Summary

[video](https://www.coursera.org/learn/gcp-fundamentals/lecture/1W4bz/review)

- GCP: a continuum of servces from **"managed infrastructure"** to **"dynamic infrastructure"**

<img src="../images/summary_GCP_continuum_managed_to_dynamic_infrastructure.png"
        alt="summary_GCP_continuum_managed_to_dynamic_infrastructure.png"
        style="float: left; margin-right: 10px;" />

- GCP offers a variety of Load balancers:

<img src="../images/various_load_balancing_services.png"
        alt="various_load_balancing_services.png"
        style="float: left; margin-right: 10px;" />

- GCP offers various ways to interconnect other networks to it:

<img src="../images/Interconnect_other_network_to_GCP.png"
        alt="Interconnect_other_network_to_GCP.png"
        style="float: left; margin-right: 10px;" />

- GCP offers various type of storage:

<img src="../images/various_storages.png"
        alt="various_storages.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/various_storages_classes.png"
        alt="various_storages_classes.png"
        style="float: left; margin-right: 10px;" />


## Resources/Articles

- [GCP vs AWS platforms](https://cloud.google.com/docs/compare/aws/#resource_management_interfaces)
- [Google Cloud Platform Fundamentals for AWS Professionals](https://www.coursera.org/learn/gcp-fundamentals-aws?mkt_tok=eyJpIjoiTXpNd1l6Sm1OakV3TlRFNCIsInQiOiI1NDJXZ2lvRGs4R1VKRlo1OThJTVVHeWFPOUxoOFN4TUpcL1kyUnQ3dm9uemhHUk9pNVcyYXJRV2pYdkJkNmlxcDc3SjFhMGRZQVVnQTFFaXJWMzBPSitkVWN6citzZUF2ZFFWQzQzcUlOVWVXaWw3c2tSXC9KR3piQTBjZU0waHV3In0%3D)
- Blog post on [Professional Cloud Architect Certification](https://medium.com/google-cloud/professional-cloud-architect-certification-6a6dfa5c6ff5) by a Googler
- [Cloud Run VS Cloud Functions: What’s the lowest cost?](https://medium.com/google-cloud/cloud-run-vs-cloud-functions-whats-the-lowest-cost-728d59345a2e)
- https://linuxacademy.com/
- [blog post comparing AWS, GCP and Azure](https://medium.com/globallogic-cloud-and-devops-blogs/clouds-compared-aws-vs-azure-vs-gcp-c59519b9d5e4)

# Essential Cloud Infrastructure: Foundation

In this module we introduce the **Architecting with Google Compute Engine specialization**.

This specialization is defined for cloud solution architects, DevOps engineers, and anyone who's interested in using GCP, to create new solutions or to integrate existing systems, application environments, and infrastructure with a focus on Compute Engine.

## Content

* [Module 1: **Introduction to GCP**](#module-1-introduction-to-gcp)
    * [GCP infrastruture](#gcp-infrastruture)
    * [Using GCP](#using-gcp)
    * [Lab 1: Console and Cloud Shell](#lab-1-console-and-cloud-shell)
    * [Projects](#projects)
    * [Lab 2: Infrastructure Preview (Jenkins with Cloud Deployment Manager in no time)](#lab-2-infrastructure-preview-jenkins-with-cloud-deployment-manager-in-no-time)
* [Module 2: **Virtual Networks**](#module-2-virtual-networks)
    * [Projects, networks, and subnetworks](#projects-networks-and-subnetworks)
    * [IP addresses](#ip-addresses)
    * [Routes and Firewall Rules](#routes-and-firewall-rules)
    * [Network Billing](#network-billing)
    * [Lab 1: Virtual Networking](#lab-1-virtual-networking)
    * [Common network designs](#common-network-designs)
    * [Need of increased Availability](#need-of-increased-availability)
    * [Globalization: Need of increased isolation against software/hardware failures](#globalization-need-of-increased-isolation-against-softwarehardware-failures)
    * [Resources in differents regions/networks/projects &amp; VPC Network Peering](#resources-in-differents-regionsnetworksprojects--vpc-network-peering)
    * [Management Separation (different projects, within same zone)](#management-separation-different-projects-within-same-zone)
    * [Bastion host isolation](#bastion-host-isolation)
    * [NAT Gateway host isolation](#nat-gateway-host-isolation)
    * [Lab 2: Bastion Host](#lab-2-bastion-host)
* [Module 3: **Virtual Machines**](#module-3-virtual-machines)
    * [What's Compute Engine?](#whats-compute-engine)
    * [What are compute options (vCPY, Memory)?](#what-are-compute-options-vcpy-memory)
    * [Compute Engine images?](#compute-engine-images)
    * [common Compute Engine actions](#common-compute-engine-actions)
* [Resources/Articles](#resourcesarticles)

## Module 1: Introduction to GCP

- [video #1](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/JrXPD/google-cloud-platform-gcp-infrastructure)
- [video #2](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/5DIZY/using-gcp)

In this module, we will provide you with an introduction to GCP by building on what you learned about the GCP infrastructure from the course introduction.

### GCP infrastruture

<img src="../images/GCP_services_continuum.png"
        alt="GCP_services_continuum.png"
        style="float: left; margin-right: 10px;" />

Analogy of infrastructure and applications:

<img src="../images/Analogy_infrastruture.png"
        alt="Analogy_infrastruture.png"
        style="float: left; margin-right: 10px;" />

4 parts covering the Cloud infrastructure:

1. **Foundation of essential infrastructure**: the basic technologies.
2. **The Core Services**: the building blocks of the essential infrastructure.'
3. **The Augmented infrastruture**: the systems built on top of the essential infrastructure, for scaling and automation.
4. **The application infrastructure**: consisted of containers and services specifically provided to make application development easy.

<img src="../images/GCP_cloud_infrastructure_domains.png"
        alt="GCP_cloud_infrastructure_domains.png"
        style="float: left; margin-right: 10px;" />

### Using GCP

Ways to interact with GCP

1. The **GCloud console** (http:://console.cloud.google.com)
2. The **Google Cloud SDK** to use `gcloud` in a terminal window
3. **CloudShell**: a browser-based terminal environment for GCP, accessible from the GCP console.


<img src="../images/3_ways_to_interact_with_GCP.png"
        alt="3_ways_to_interact_with_GCP.png"
        style="float: left; margin-right: 10px;" />

Working with other client libraries:

<img src="../images/GCP_client_libraries.png"
        alt="GCP_client_libraries.png"
        style="float: left; margin-right: 10px;" />


### Lab 1: Console and Cloud Shell

- video lab
- [notes lab](../labs/lab_console_cloudshell.md)


### Projects

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/aqJJ9/demo-projects)

### Lab 2: Infrastructure Preview (Jenkins with Cloud Deployment Manager in no time)

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/xTlIl/lab-2-infrastructure-preview-overview-and-objectives)








## Module 2: Virtual Networks

In this module, we start by introducing **Virtual Private Cloud (VPC)** which is Google’s **_managed networking functionality_** for your Cloud Platform resources. Then we dissect networking into its fundamental components, which are:

- projects,
- networks,
- subnetworks,
- IP addresses,
- routes and firewall rules,
- along with network pricing.

- [video #1: Google Cloud Platform (GCP) VPC](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/vJbfe/google-cloud-platform-gcp-vpc)
- [video #2: Projects, networks, and subnetworks](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/FyKc4/projects-networks-and-subnetworks)


### Projects, networks, and subnetworks

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/FyKc4/projects-networks-and-subnetworks)

<img src="../images/Example_5_networks_and_interconnections.png"
        alt="Example_5_networks_and_interconnections.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Example_5_networks_and_interconnections_regions_and_zones.png"
        alt="Example_5_networks_and_interconnections_regions_and_zones.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Example_5_subnetworks_managing_resources.png"
        alt="Example_5_subnetworks_managing_resources.png"
        style="float: left; margin-right: 10px;" />

### IP addresses

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/VBh8c/ip-addresses)

<img src="../images/IP_addresses.png"
        alt="IP_addresses.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/External_IP_addresses_always_mapped_to_internal_IP_Addresses.png"
        alt="External_IP_addresses_always_mapped_to_internal_IP_Addresses.png"
        style="float: left; margin-right: 10px;" />

In case of restart, the internal IP address may change, but the DNS system points to instances which keep the external IP address unchanged.

### Routes and Firewall Rules

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/WrQIK/routes-and-rules)

A route is  a mapping of an IP range to a destination.

### Network Billing

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/9uFtR/billing)

### Lab 1: Virtual Networking 


Compare and explore a complex GCP network structure.

- you build a complex network topology

<img src="../images/lab_network_diagram.png"
        alt="lab_network_diagram.png"
        style="float: left; margin-right: 10px;" />

- you will launch VMs in varius network/sub-networks

<img src="../images/lab_network_launch_VMs_in_various_networks.png"
        alt="lab_network_launch_VMs_in_various_networks.png"
        style="float: left; margin-right: 10px;" />

- you will ping VMs accross the networks

<img src="../images/lab_network_ping_various_part_of_network.png"
        alt="lab_network_ping_various_part_of_network.png"
        style="float: left; margin-right: 10px;" />


[lab. details](../labs/lab_complx_network_on_GCP.md)







### Common network designs

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/OeuYo/common-network-designs)

How these elements work together:

* projects
* networks
* subnetworks
* regions
* zones

 
In short, they provide a rich set of:

 * alternatives for managing groups of resources with varying availability
 * and access control requirements.

So you can work globally or work at a very granular level if you want/need to.

#### Need of increased Availability

<img src="../images/networking_availability.png"
        alt="networking_availability.png"
        style="float: left; margin-right: 10px;" />

#### Globalization: Need of increased isolation against software/hardware failures

<img src="../images/networking_globalization.png"
        alt="networking_globalization.png"
        style="float: left; margin-right: 10px;" />

#### Resources in differents regions/networks/projects & VPC Network Peering

- **Region/Network/Proect isolated services** >>> preventing compromised of one part from spreading to other parts.
- **VPC Network Peering** >>> Allows these services can still communicate over a private address space.

<img src="../images/networking_globalization_different_subnets.png"
        alt="networking_globalization_different_subnets.png"
        style="float: left; margin-right: 10px;" />

#### Management Separation (different projects, within same zone)

VMs isolated into separate projects, but within the same zone, useful for **Identity and Access Management**.

You can assign different people to different roles (for management separation) for each project, limiting the access to the network they need access to.

<img src="../images/networking_project_management.png"
        alt="networking_project_management.png"
        style="float: left; margin-right: 10px;" />

> This allows granular access management per sub-project for a better access control,
> 
> But remember than a network can NOT span Projects... so the projects NEED to communicate via the internet!



#### Bastion host isolation

<img src="../images/networking_bastion_host_isolation.png"
        alt="networking_bastion_host_isolation.png"
        style="float: left; margin-right: 10px;" />

#### NAT Gateway host isolation

Let's one network/project/"VM instance" to not access internet. Therefore this allows Instance 1 to communicate with another instance on a separate network via the gateway.

The two networks do not have to be in the same project for this design to work.

<img src="../images/networking_NAT_gateway_host_isolation.png"
        alt="networking_NAT_gateway_host_isolation.png"
        style="float: left; margin-right: 10px;" />


#### Lab 2: Bastion Host

- [video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/qfyZl/lab-2-bastion-host-overview-and-objectives)

Removing the connection to the internet of a webserver meant to deliver services only to a corporate audience.

<img src="../images/lab_network_bastion_host.png"
        alt="lab_network_bastion_host.png"
        style="float: left; margin-right: 10px;" />


[lab notes](../labs/lab_Networking_Bastion_host.md)

> There are other security alternatives to provide routine administration access to web server like using **Cloud VPN**, which is covered in a later course of this specialization.





## Module 3: Virtual Machines

[intro video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/zZPUh/module-overview-intro)

In this module, we cover **virtual machine instances**, or **VMs**.

First we'll start with:

- the **basics of Compute Engine**, followed by a quick little lab to get you more familiar with creating virtual machines.
- Then, we’ll look at the **different CPU and memory options** that enable you to create different configurations.
- Next, we will look at images and the **different disk options available with Compute Engine**.
- After that, we will discuss very **common Compute Engine actions** that you might encounter in your day-to-day job.

This will be followed by an in-depth lab that explores many of the features and services covered in this module.


### What's Compute Engine?

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/7Yk7C/compute-engine)

<img src="../images/Compute_engine_in_GCP_Compute_spectrum.png"
        alt="Compute_engine_in_GCP_Compute_spectrum.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Compute_engine_what_it_is.png"
        alt="Compute_engine_what_it_is.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Compute_engine_features.png"
        alt="Compute_engine_features.png"
        style="float: left; margin-right: 10px;" />


#### Compute options

<img src="../images/Compute_engine_Compute_options.png"
        alt="Compute_engine_Compute_options.png"
        style="float: left; margin-right: 10px;" />

#### Disk (Storage) options

<img src="../images/Compute_engine_Disk_options.png"
        alt="Compute_engine_Disk_options.png"
        style="float: left; margin-right: 10px;" />


#### Networking options

<img src="../images/Compute_engine_Networking_options.png"
        alt="Compute_engine_Networking_options.png"
        style="float: left; margin-right: 10px;" />

#### Demo Compute Engine options

- [video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/5NGzq/demo-compute-engine)

#### Pricing and discounts

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/2B8Tb/pricing-and-discounts) 

<img src="../images/Compute_engine_pricing.png"
        alt="Compute_engine_pricing.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Compute_engine_pricing_VM_discounts.png"
        alt="Compute_engine_pricing_VM_discounts.png"
        style="float: left; margin-right: 10px;" />

Example of cumulated usage for calculating **"sustained-use" discounts**: 

<img src="../images/Compute_engine_pricing_VM_discounts_example_of_cumulated_usage.png"
        alt="Compute_engine_pricing_VM_discounts_example_of_cumulated_usage.png"
        style="float: left; margin-right: 10px;" />

#### VM access and lifecycle

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/CGmcv/vm-access-and-lifecycle)


<img src="../images/Compute_engine_VM_access_Linux_Windows.png"
        alt="Compute_engine_VM_access_Linux_Windows.png"
        style="float: left; margin-right: 10px;" />

VM lifecycle:

<img src="../images/Compute_engine_VM_lifecycle.png"
        alt="Compute_engine_VM_lifecycle.png"
        style="float: left; margin-right: 10px;" />

Changing VM's state from "running": 

<img src="../images/Compute_engine_VM_change_of_state_from_running.png"
        alt="Compute_engine_VM_change_of_state_from_running.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Compute_engine_VM_possible_auto_live_migration.png"
        alt="Compute_engine_VM_possible_auto_live_migration.png"
        style="float: left; margin-right: 10px;" />

Stopped VM (No charge):

<img src="../images/Compute_engine_VM_stopped.png"
        alt="Compute_engine_VM_stopped.png"
        style="float: left; margin-right: 10px;" />

#### Lab 1 Creating Virtual Machines

- [video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/vc4nH/lab-1-creating-virtual-machines-overview-and-objectives)
- [lab notes](../labs/lab_VMS_Linux_Windows.md)



### What are compute options (vCPY, Memory)?

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/JjM0D/compute-options)

Compute engine 3 options to create VMs: 

<img src="../images/Compute_engine_3_options_to_create_VMs.png"
        alt="Compute_engine_3_options_to_create_VMs.png"
        style="float: left; margin-right: 10px;" />

Compute engine 4 classes of VMs:

<img src="../images/Compute_engine_4_classes_of_VMs.png"
        alt="Compute_engine_4_classes_of_VMs.png"
        style="float: left; margin-right: 10px;" />


Compute engine 80% on preemptible VMs (24hours max):

<img src="../images/Compute_engine_80%_on_preemptible_VMs.png"
        alt="Compute_engine_80%_on_preemptible_VMs.png"
        style="float: left; margin-right: 10px;" />

There exists ways to monitr and restart preemptible VMs even though this doesn't come as a default option. 


### Compute Engine (disk) images?

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/To7uo/images)

<img src="../images/Compute_engine_disk_image.png"
        alt="Compute_engine_disk_image.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/Compute_engine_disk_image_private_or_public.png"
        alt="Compute_engine_disk_image_private_or_public.png"
        style="float: left; margin-right: 10px;" />

### Compute Engine Disk options

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/5Ibi2/disk-options)

<img src="../images/Compute_engine_disk_image_boot_image.png"
        alt="Compute_engine_disk_image_boot_image.png"
        style="float: left; margin-right: 10px;" />

#### Persistent disks

- bounded to their zone
- dynamically resizable, even when running!

<img src="../images/Compute_engine_disk_image_boot_image_persistent.png"
        alt="Compute_engine_disk_image_boot_image_persistent.png"
        style="float: left; margin-right: 10px;" />

#### Local SSD disks 

- data will survive a RESET
- data will NOT survive a STOP or TERMINATE (because these disks can't be re-attached to a different VM)

#### RAM disk
fastest, for low needs in memory.


#### Summary

<img src="../images/Compute_engine_disk_image_summary.png"
        alt="Compute_engine_disk_image_summary.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/Compute_engine_disk_max_disk_for_max_cores.png"
        alt="Compute_engine_disk_max_disk_for_max_cores.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/Compute_engine_disk_differences_cloud_vs_physical_disks.png"
        alt="Compute_engine_disk_differences_cloud_vs_physical_disks.png"
        style="float: left; margin-right: 10px;" />

### common Compute Engine actions

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/sdGf3/common-compute-engine-actions)


#### Moving an instance to a new zone

<img src="../images/Compute_engine_actions_moving_zones.png"
        alt="Compute_engine_actions_moving_zones.png"
        style="float: left; margin-right: 10px;" />
 

<img src="../images/Compute_engine_actions_moving_zones_automated.png"
        alt="Compute_engine_actions_moving_zones_automated.png"
        style="float: left; margin-right: 10px;" />

#### Snapshots

##### disk backup

<img src="../images/Compute_engine_actions_snapshots_disk_backup.png"
        alt="Compute_engine_actions_snapshots_disk_backup.png"
        style="float: left; margin-right: 10px;" />

##### data migration between zones

<img src="../images/Compute_engine_actions_snapshots_data_migration.png"
        alt="Compute_engine_actions_snapshots_data_migration.png"
        style="float: left; margin-right: 10px;" />

##### change disk type (HDD <> SSD)

<img src="../images/Compute_engine_actions_snapshots_change_disk_type.png"
        alt="Compute_engine_actions_snapshots_change_disk_type.png"
        style="float: left; margin-right: 10px;" />

#### Safe snapshot preparation

<img src="../images/Compute_engine_actions_safe_snapshots_preparation.png"
        alt="Compute_engine_actions_safe_snapshots_preparation.png"
        style="float: left; margin-right: 10px;" />

#### Resize persistent disk

<img src="../images/Compute_engine_actions_sresize_disk.png"
        alt="Compute_engine_actions_sresize_disk.png"
        style="float: left; margin-right: 10px;" />

### Lab 2 Working with VM: setup a gaming application server

- [video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/eazN4/lab-2-working-with-virtual-machines-overview-and-objectives)


Build the infrastructure needed for production activities:

- Backups
- graceful shutdown/restart services

[Lab notes](../labs/lab_VM_backups_application_in_production.md) & [video lab review](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/0ZuCj/lab-2-working-with-virtual-machines-review)


### Module 3 review

[video](https://www.coursera.org/learn/gcp-infrastructure-foundation/lecture/RZE3H/module-3-review)

## Resources/Articles

- IP Addresses: https://cloud.google.com/compute/docs/ip-addresses/
- Subnets and CIDR ranges: https://cloud.google.com/compute/docs/alias-ip/#subnets_and_cidr_ranges

# Essential Cloud Infrastructure: Core Services


The goal of these courses is:

* to remember and understand the **different GCP services** and **features** and also
* to be able to apply your knowledge, 
* to analyze requirements,
* to evaluate different options, and 
* to create your own services.

This course builds on the [Essential Cloud Infrastructure: Foundation](./cloud_architect/course_2_Essential_Cloud_Infrastructure__Foundation.md) course and enhances your study of architecting with Compute Engine. In this course, we start by talking about Cloud IAM, and you will administer Identity and Access Management for resources. Next, we’ll cover the different data storage services in GCP, and you will implement some of those services. Then, we’ll go over resource management, where you will manage and examine billing of GCP resources. Lastly, we’ll talk about resource monitoring, and you will monitor GCP resources using Stackdriver services. 


> "We want to welcome you to Architecting with Compute Engine".

## Content

- [course intro video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/6Zi73/course-introduction)
- [course review video on storage/database services](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/EismW/module-review)
- [Module review video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/tLWuy/course-review)


* [Cloud Identity and Access Management (Cloud IAM)](#cloud-identity-and-access-management-cloud-iam)
    * [Organizations](#organizations)
    * [Folders: sub-organizations](#folders-sub-organizations)
    * [Roles](#roles)
    * [Demo: Create a Custom role in GCP](#demo-create-a-custom-role-in-gcp)
    * [Members](#members)
    * [Service Accounts](#service-accounts)
    * [Scopes](#scopes)
    * [Cloud IAM best practices](#cloud-iam-best-practices)
    * [Cloud IAP](#cloud-iap)
    * [Lab Intro: Cloud IAM](#lab-intro-cloud-iam)
* [Data Storage Services](#data-storage-services)
    * [Cloud Storage](#cloud-storage)
    * [Cloud Storage lab](#cloud-storage-lab)
    * [Cloud SQL](#cloud-sql)
    * [Cloud SQL lab](#cloud-sql-lab)
    * [Cloud Spanner](#cloud-spanner)
    * [Cloud Firestore](#cloud-firestore)
    * [Cloud Bigtable](#cloud-bigtable)
    * [Cloud Memorystore (Redis)](#cloud-memorystore-redis)
* [Resource Management](#resource-management)
    * [Cloud Resource](#cloud-resource)
    * [Quotas](#quotas)
    * [Labels and names](#labels-and-names)
    * [Billing](#billing)
    * [Use Labels to optimize spendings](#use-labels-to-optimize-spendings)
    * [Lab: Billing Administration](#lab-billing-administration)
* [Resource Monitoring](#resource-monitoring)
    * [StackDriver Overview](#stackdriver-overview)
    * [Monitoring with StackDriver](#monitoring-with-stackdriver)
    * [SRE: Site Reliability Engineering](#sre-site-reliability-engineering)
    * [Lab. Resource Monitoring with StackDriver](#lab-resource-monitoring-with-stackdriver)
    * [Logging with Stackdriver](#logging-with-stackdriver)
    * [Error Reporting with Stackdriver](#error-reporting-with-stackdriver)
    * [Tracing with Stackdriver](#tracing-with-stackdriver)
    * [Debugging with Stackdriver](#debugging-with-stackdriver)
    * [Lab: Error Reporting and Debugging with Stackdriver](#lab-error-reporting-and-debugging-with-stackdriver)
* [Resources/Articles### Debugging with Stackdriver](#resourcesarticles-debugging-with-stackdriver)



-  more than one solution for a task or application in GCP, a [solution continuum](https://github.com/Patechoc/GCP_memo/blob/master/cloud_architect/course_2_Essential_Cloud_Infrastructure__Foundation.md#gcp-infrastruture)
- Infrastructure, Users, Applications [analogy](https://github.com/Patechoc/GCP_memo/blob/master/cloud_architect/course_2_Essential_Cloud_Infrastructure__Foundation.md#gcp-infrastruture)

GCP offers a **range of Compute Services**

<img src="../images/core_services_Compute_Services.png"
        alt="core_services_Compute_Services.png"
        style="float: left; margin-right: 10px;" />


## Cloud Identity and Access Management (Cloud IAM)

- [Cloud IAM overview](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/UbUc3/cloud-iam)

Cloud IAM is a sophisticated system built on top of.

- email-like address names,
- job type roles in granular permissions.

Components within Cloud IAM which are **organizations**, **roles**, **members** and **service accounts**


[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/UbUc3/cloud-iam) 

Who can do What on Which resources:

<img src="../images/core_services_Cloud_IAM_Who_DoWhat_WhichResource.png"
        alt="core_services_Cloud_IAM_Who_DoWhat_WhichResource.png"
        style="float: left; margin-right: 10px;" />


Cloud IAM objects: 

<img src="../images/core_services_Cloud_IAM_objects.png"
        alt="core_services_Cloud_IAM_objects.png"
        style="float: left; margin-right: 10px;" />


Cloud IAM resource hierarchy:

<img src="../images/core_services_Cloud_IAM_resource_hierarchy.png"
        alt="core_services_Cloud_IAM_resource_hierarchy.png"
        style="float: left; margin-right: 10px;" />

> Apply the **Principle of Least Priviledges**: Always select the smallest scope that's necessary for the task in order to reduce your exposure to risk!

### Organizations

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/M0m2G/organization)

- **"Organization Admin"**
- **"Project Creator"**

<img src="../images/core_services_Cloud_IAM_resource_Organization.png"
        alt="core_services_Cloud_IAM_resource_Organization.png"
        style="float: left; margin-right: 10px;" />

Responsabilities of:

- **"Cloud Identity account manager"**
- **"Organization Admin"**

<img src="../images/core_services_GCP_resources.png"
        alt="core_services_GCP_resources.png"
        style="float: left; margin-right: 10px;" />


### Folders: sub-organizations

Folders can act as a sub-organization wihtin the organization.

<img src="../images/core_services_Cloud_IAM_resource_Folders.png"
        alt="core_services_Cloud_IAM_resource_Folders.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/core_services_Cloud_IAM_resource_every_Roles_of_a_project.png"
        alt="core_services_Cloud_IAM_resource_every_Roles_of_a_project.png"
        style="float: left; margin-right: 10px;" />


### Roles

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/rgNsR/roles)

= Roles define the can do what on which resource part of Cloud IAM


There are three types of roles in Cloud IAM; **Primitive roles**, **predefined roles**, and **custom roles**:

<img src="../images/core_services_Cloud_IAM_Roles.png"
        alt="core_services_Cloud_IAM_Roles.png"
        style="float: left; margin-right: 10px;" />

- **Primitive roles** are the original roles that were available in the GCP console, but they are broad. You apply them to a GCP project and they affect all resources in that project.

<img src="../images/core_services_Cloud_IAM_Roles_primitive.png"
        alt="core_services_Cloud_IAM_Roles_primitive.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/core_services_Cloud_IAM_Roles_primitive_coarse_grained.png"
        alt="core_services_Cloud_IAM_Roles_primitive_coarse_grained.png"
        style="float: left; margin-right: 10px;" />

- **Predefined roles** define where those roles can be applied. This provides members with granular access to specific GCP resources and prevents unwanted access to other resources. These roles are collections of permissions because to do any meaningful operations, you usually need more than one permission.

<img src="../images/core_services_Cloud_IAM_Roles_predefined.png"
        alt="core_services_Cloud_IAM_Roles_predefined.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/core_services_Cloud_IAM_Roles_predefined_ex.png"
        alt="core_services_Cloud_IAM_Roles_predefined_ex.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/core_services_Cloud_IAM_Roles_predefined_all.png"
        alt="core_services_Cloud_IAM_Roles_predefined_all.png"
        style="float: left; margin-right: 10px;" />

But what if one of those roles does not have enough permissions or you need something even finer-grained?

That's what **Custom Roles** permit: a lot of companies use the **least privileged model** in which each person in your organization is given the minimal amount of privilege needed to do their job.

<img src="../images/core_services_Cloud_IAM_Roles_custom.png"
        alt="core_services_Cloud_IAM_Roles_custom.png"
        style="float: left; margin-right: 10px;" />

#### Demo: Create a Custom role in GCP

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/3bQES/demo-custom-roles)



### Members

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/4vrs0/members)

= **Members** define the who part, of who can do what, on which resource.

<img src="../images/core_services_Cloud_IAM_Members.png"
        alt="core_services_Cloud_IAM_Members.png"
        style="float: left; margin-right: 10px;" />




There are 5 different types of members:

- **Google Accounts**: a Google Account represents a developer, an administrator or any other person who interacts with GCP
- **Service Accounts**,
- **Google Groups**,
- **G Suite Domains**, and
- **Cloud Identity Domains**. 


 What if you already have a different corporate directory? How can you get your users and groups into GCP? 
 
Use **Google Cloud Directory Sync**!!

<img src="../images/core_services_Cloud_IAM_remote_LDAP_Members.png"
        alt="core_services_Cloud_IAM_remote_LDAP_Members.png"
        style="float: left; margin-right: 10px;" />


Many ways to sync your remote account:

<img src="../images/core_services_Cloud_IAM_remote_LDAP_Members_SSO.png"
        alt="core_services_Cloud_IAM_remote_LDAP_Members_SSO.png"
        style="float: left; margin-right: 10px;" />




### Service Accounts

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/292ex/service-accounts)


 A service account is an account that belongs to your application instead of to an individual end user

<img src="../images/core_services_Cloud_IAM_service_account_id.png"
        alt="core_services_Cloud_IAM_service_account_id.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/core_services_Cloud_IAM_service_account_default_for_app_engine.png"
        alt="core_services_Cloud_IAM_service_account_default_for_app_engine.png"
        style="float: left; margin-right: 10px;" />

 
#### Scopes

<img src="../images/core_services_Cloud_IAM_service_account_scope.png"
        alt="core_services_Cloud_IAM_service_account_scope.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/core_services_Cloud_IAM_user_created_service_accounts_only_predefined_roles.png"
        alt="core_services_Cloud_IAM_user_created_service_accounts_only_predefined_roles.png"
        style="float: left; margin-right: 10px;" />


Services Accounts use keys:

<img src="../images/core_services_Cloud_IAM_service_accounts_use_keys.png"
        alt="core_services_Cloud_IAM_service_accounts_use_keys.png"
        style="float: left; margin-right: 10px;" />

### Cloud IAM best practices

- [Module intro video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/xghL2/cloud-iam-best-practices)
- [Module Review video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/u8ETv/module-review)

<img src="../images/core_services_Cloud_IAM_best_practices_resource_hierarchy.png"
        alt="core_services_Cloud_IAM_best_practices_resource_hierarchy.png"
        style="float: left; margin-right: 10px;" />

Grant roles to groups instead of individuals:

<img src="../images/core_services_Cloud_IAM_best_practices_groups.png"
        alt="core_services_Cloud_IAM_best_practices_groups.png"
        style="float: left; margin-right: 10px;" />


Example of best practices when using Service Accounts:

<img src="../images/core_services_Cloud_IAM_best_practices_example_service_Accounts.png"
        alt="core_services_Cloud_IAM_best_practices_example_service_Accounts.png"
        style="float: left; margin-right: 10px;" />

#### Cloud IAP


Cloud IAP lets you establish a central authorization layer for applications accessed by HTTPS.
So you can use an application level access control model instead of relying on network level firewalls. Applications and resources protected by Cloud IAP can only be accessed through the proxy by users and groups with the correct Cloud IAM role. 


<img src="../images/core_services_Cloud_IAM_best_practices_Cloud_IAP.png"
        alt="core_services_Cloud_IAM_best_practices_Cloud_IAP.png"
        style="float: left; margin-right: 10px;" />

### Lab Intro: Cloud IAM

- [lab notes](../labs/lab_Cloud_IAM.md)
- [walkthrough video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/mpXBr/lab-review-cloud-iam)


## Data Storage Services

- [Module intro video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/HBW4r/module-overview)
- Module Review video


The purpose of this module is to explain which services are available and when to consider using them from an **infrastructure perspective**.

> "I want you to be able to set up and connect to a service without detailed knowledge of how to use a database system. If you want a deeper dive into the design, organizations, structures, schemas, and details on how data can be optimized,served, and stored properly within those different services, I recommend **Google Cloud's data engineering courses**"

<img src="../images/core_services_Data_Storage_module_scope.png"
        alt="core_services_Data_Storage_module_scope.png"
        style="float: left; margin-right: 10px;" />


Google offers several storage services to choose from:

- Cloud Storage
- Cloud SQL
- Cloud Spanner
- Cloud Firestore
- and Cloud Bigtable.

<img src="../images/core_services_Data_Storage_services.png"
        alt="core_services_Data_Storage_services.png"
        style="float: left; margin-right: 10px;" />


Choose using this decision tree:

<img src="../images/core_services_Data_Storage_services_decision_tree.png"
        alt="core_services_Data_Storage_services_decision_tree.png"
        style="float: left; margin-right: 10px;" />

### Cloud Storage

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/MXyDu/cloud-storage)

Overview of storage classes:

- Regional
- Multi-regional
- Nearline
- Coldline

<img src="../images/core_services_Data_Storage_storage_classes.png"
        alt="core_services_Data_Storage_storage_classes.png"
        style="float: left; margin-right: 10px;" />


Cloud Storage entities:

- buckets
- objects
- access

<img src="../images/core_services_Data_Storage_storage_entities.png"
        alt="core_services_Data_Storage_storage_entities.png"
        style="float: left; margin-right: 10px;" />


Changing default storage class:

<img src="../images/core_services_Data_Storage_storage_changing_classes.png"
        alt="core_services_Data_Storage_storage_changing_classes.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/core_services_Data_Storage_storage_access_control.png"
        alt="core_services_Data_Storage_storage_access_control.png"
        style="float: left; margin-right: 10px;" />

Zooming on ACL (Access Control Lists) = Who can access your bucket and what they can do (100 ACLs max). 

<img src="../images/core_services_Data_Storage_storage_access_control_ACLs.png"
        alt="core_services_Data_Storage_storage_access_control_ACLs.png"
        style="float: left; margin-right: 10px;" />


Limited-time access to a user:

`gsutil signurl -d 10m path/to/privatekey.p12 gs://bucket/object`

<img src="../images/core_services_Data_Storage_storage_limited_time_Access_to_user.png"
        alt="core_services_Data_Storage_storage_limited_time_Access_to_user.png"
        style="float: left; margin-right: 10px;" />

Cloud Storage Features

([video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/wKUHL/cloud-storage-features))

<img src="../images/core_services_Data_Storage_storage_features.png"
        alt="core_services_Data_Storage_storage_features.png"
        style="float: left; margin-right: 10px;" />


Object versioning (OFF by default)

<img src="../images/core_services_Data_Storage_storage_features_object_versioning.png"
        alt="core_services_Data_Storage_storage_features_object_versioning.png"
        style="float: left; margin-right: 10px;" />

Object lifecycle management (rule-based actions: e.g. delete an object after a year, ...)

<img src="../images/core_services_Data_Storage_storage_features_object_lifecycle_management.png"
        alt="core_services_Data_Storage_storage_features_object_lifecycle_management.png"
        style="float: left; margin-right: 10px;" />

Object Notification with webhooks

<img src="../images/core_services_Data_Storage_storage_features_object_change_notifications.png"
        alt="core_services_Data_Storage_storage_features_object_change_notifications.png"
        style="float: left; margin-right: 10px;" />

Data Import services (TeraBytes of data):

- **Transfer Appliance** (hardware appliance from 100TB to 1 PetaBytes)
- **Storage Transfer Service** (from online data, e.g. from AWS bucket)
- **Offline Media Import**: 3rd party provider uploads data from physical media 

<img src="../images/core_services_Data_Storage_storage_features_data_import_services.png"
        alt="core_services_Data_Storage_storage_features_data_import_services.png"
        style="float: left; margin-right: 10px;" />

Decision tree to choose your storage class

<img src="../images/core_services_Data_Storage_storage_decision_tree_class_storage.png"
        alt="core_services_Data_Storage_storage_decision_tree_class_storage.png"
        style="float: left; margin-right: 10px;" />


### Cloud Storage lab

- [lab tasks description](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/bcncM/lab-intro-cloud-storage)
- [lab notes](../labs/lab_Cloud_Storage.md)
- [Lab Review: Cloud Storage](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/6IAAh/lab-review-cloud-storage)

### Cloud SQL

- [module intro video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/cMja1/cloud-sql)

Cloud SQL is a **"managed service"** offering an _SQL database_ **service**.

<img src="../images/core_services_cloudSQL_manage_service.png"
        alt="core_services_cloudSQL_manage_service.png"
        style="float: left; margin-right: 10px;" />

Performances
<img src="../images/core_services_cloudSQL_performance.png"
        alt="core_services_cloudSQL_performance.png"
        style="float: left; margin-right: 10px;" />

Optional features (backup, automatic failover, import/export and scaling)

<img src="../images/core_services_cloudSQL_optional_features.png"
        alt="core_services_cloudSQL_optional_features.png"
        style="float: left; margin-right: 10px;" />

Connecting to a Cloud SQL instance (Summarized in a decision tree for Best Practices)

<img src="../images/core_services_cloudSQL_connecting_to_CloudSQL_instance.png"
        alt="core_services_cloudSQL_connecting_to_CloudSQL_instance.png"
        style="float: left; margin-right: 10px;" />

Decision tree for your SQL storage

<img src="../images/core_services_cloudSQL_choosing_your_SQL_storage.png"
        alt="core_services_cloudSQL_choosing_your_SQL_storage.png"
        style="float: left; margin-right: 10px;" />


### Cloud SQL lab

- [lab tasks description](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/caD6h/lab-intro-cloud-sql)
- [lab notes](../labs/lab_Cloud_SQL.md)
- [Lab Review: Cloud SQL (MySQL)](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/1Il73/lab-review-cloud-sql)

<img src="../images/lab_Cloud_SQL_01.png"
        alt="lab_Cloud_SQL_01.png"
        style="float: left; margin-right: 10px;" />



### Cloud Spanner

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/gu1Xc/cloud-spanner)

<img src="../images/lab_Cloud_Spanner_features.png"
        alt="lab_Cloud_Spanner_features.png"
        style="float: left; margin-right: 10px;" />

Best of Relational & non-relational DB world

<img src="../images/lab_Cloud_Spanner_characteristics_best_relational_non_relational_worlds.png"
        alt="lab_Cloud_Spanner_characteristics_best_relational_non_relational_worlds.png"
        style="float: left; margin-right: 10px;" />

This architecture allows for high availability and global placement:

<img src="../images/lab_Cloud_Spanner_architecture.png"
        alt="lab_Cloud_Spanner_architecture.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/lab_Cloud_Spanner_Decision_tree_to_choose_Spanner.png"
        alt="lab_Cloud_Spanner_Decision_tree_to_choose_Spanner.png"
        style="float: left; margin-right: 10px;" />



### Cloud Firestore

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/Z0QRZ/cloud-firestore)

Cloud Firestore is a:
- fast,
- fully managed,
- serverless Cloud native,
- NoSQL document database,
- that simplifies storing, sinking, and querying data for your mobile, web, and IoT apps at global scale

<img src="../images/lab_Cloud_Firestore.png"
        alt="lab_Cloud_Firestore.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/lab_Cloud_Firestore_new_Datastore.png"
        alt="lab_Cloud_Firestore_new_Datastore.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/lab_Cloud_FireStore_Decision_tree_to_choose_FireStore.png"
        alt="lab_Cloud_FireStore_Decision_tree_to_choose_FireStore.png"
        style="float: left; margin-right: 10px;" />


### Cloud Bigtable

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/98vuS/cloud-bigtable)

<img src="../images/lab_Cloud_BigTable.png"
        alt="lab_Cloud_BigTable.png"
        style="float: left; margin-right: 10px;" />


Cloud Bigtable stores data in massively scalable tables:
- each of which is a sorted key value map.
- The table is composed of rows, each of which typically describes a single entity, - columns which contain individual values for each row.
- Each row is indexed by a single row key.
- Columns that are related to one another are typically grouped together into a column family.
- Each column is identified by a combination of the column family and a column qualifier which is a unique name within the column family.
- Each row column intersection can contain multiple cells or versions at different timestamps, providing a record of how the stored data has been altered over time. 


<img src="../images/lab_Cloud_BigTable_storage_model.png"
        alt="lab_Cloud_BigTable_storage_model.png"
        style="float: left; margin-right: 10px;" />

Processing is separated from storage:

<img src="../images/lab_Cloud_BigTable_storage_model_overal_architechture.png"
        alt="lab_Cloud_BigTable_storage_model_overal_architechture.png"
        style="float: left; margin-right: 10px;" />


Linear scaling of data re-distribution with number of nodes:

<img src="../images/lab_Cloud_BigTable_storage_model_overal_architechture_auto_rebalance.png"
        alt="lab_Cloud_BigTable_storage_model_overal_architechture_auto_rebalance.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/lab_Cloud_BigTable_Decision_tree_to_choose_BigTable.png"
        alt="lab_Cloud_BigTable_Decision_tree_to_choose_BigTable.png"
        style="float: left; margin-right: 10px;" />



### Cloud Memorystore (Redis)

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/Vh6cS/cloud-memorystore)


<img src="../images/lab_Cloud_MemoryStore_Redis.png"
        alt="lab_Cloud_MemoryStore_Redis.png"
        style="float: left; margin-right: 10px;" />


## Resource Management

= Manage and examine **Billing** of GCP resources

- [module overview](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/jPfvH/module-overview)
- [module review](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/tJOrj/module-review)


### Cloud Resource

- [video Resource Manager](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/ubZCA/cloud-resource-manager)

In this module, we will cover resource management.
Resources and GCP are billable, so **managing resources means controlling cost**. There are several methods in place for controlling access to the resources and there are quotas that limit consumption

Overview of Resource Manager ([video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/ubZCA/cloud-resource-manager))

<img src="../images/lab_Cloud_ResourceManager.png"
        alt="lab_Cloud_ResourceManager.png"
        style="float: left; margin-right: 10px;" />

Root Node = Organization node:

<img src="../images/lab_Cloud_ResourceManager_root_node_organization.png"
        alt="lab_Cloud_ResourceManager_root_node_organization.png"
        style="float: left; margin-right: 10px;" />

From a physical organization standpoint, resources are categorized as:

- global,
- regional or
- zonal.

Let's look at some examples. Images, snapshots, and networks, are global resources. 

External IP addresses are regional resources, and instances and disks are zonal resources. However, regardless of the type, each resource is organized into a project. This enables each project to have its own billing and reporting.

<img src="../images/lab_Cloud_ResourceManager_what_can_be_tracked.png"
        alt="lab_Cloud_ResourceManager_what_can_be_tracked.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/lab_Cloud_ResourceManager_regional_zonal.png"
        alt="lab_Cloud_ResourceManager_regional_zonal.png"
        style="float: left; margin-right: 10px;" />


### Quotas

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/cVawh/quotas)

<img src="../images/lab_Resources_Quotas.png"
        alt="lab_Resources_Quotas.png"
        style="float: left; margin-right: 10px;" />

Why quotas?

- protection against high bills
- prevent billing spikes
- forces sizing considerations

<img src="../images/lab_Resources_Quotas_why.png"
        alt="lab_Resources_Quotas_why.png"
        style="float: left; margin-right: 10px;" />


### Labels and names

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/kklUj/labels-and-names)

Projects and folders provide levels of segregation for resources. But what if you want more granularity?

That's where labels and names come in.

- **Labels are a utility for organizing GCP resources**.
- **Labels are key value pairs** that you can attach to your resources like VMs, disks, snapshots, and images.

<img src="../images/lab_Resources_Labels.png"
        alt="lab_Resources_Labels.png"
        style="float: left; margin-right: 10px;" />

What to use them for?

<img src="../images/lab_Resources_Labels_example_usage.png"
        alt="lab_Resources_Labels_example_usage.png"
        style="float: left; margin-right: 10px;" />


Labels vs Tags

<img src="../images/lab_Resources_Labels_vs_tags.png"
        alt="lab_Resources_Labels_vs_tags.png"
        style="float: left; margin-right: 10px;" />

### Billing

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/PiRrk/billing)

<img src="../images/lab_Resources_budget_creation_interface.png"
        alt="lab_Resources_budget_creation_interface.png"
        style="float: left; margin-right: 10px;" />

#### Use Labels to optimize spendings

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/PiRrk/billing)

Maybe these instances are sending most of their traffic to a different continent which could incur higher cost.

In that case, you might consider relocating some of those instances or using a caching service like Cloud CDN to cach content closer to your users, which reduces your networking spend. 

> **Google recommends labeling all your resources and exporting your billing data to BigQuery to analyze your spend.**

<img src="../images/lab_Resources_budget_use_Labels_to_optimize_spending.png"
        alt="lab_Resources_budget_use_Labels_to_optimize_spending.png"
        style="float: left; margin-right: 10px;" />

Visualize your spends with Data Studio

<img src="../images/lab_Resources_budget_visualize_spendings_over_time_DataStudio.png"
        alt="lab_Resources_budget_visualize_spendings_over_time_DataStudio.png"
        style="float: left; margin-right: 10px;" />

### Lab: Billing Administration

- [video billing administration](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/xpHII/demo-billing-administration)
- [video Lab Intro: Examining **Billing Data** with **BigQuery**](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/Nz755/lab-intro-examining-billing-data-with-bigquery)
- [Lab notes: Billing data with BigQuery](../labs/lab_billing_data_with_BigQuery.md)
- [Lab Review: Examining Billing Data with BigQuery](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/As3u1/lab-review-examining-billing-data-with-bigquery)



## Resource Monitoring

- [video module intro](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/yCn32/module-overview)
- [Module review on Resource Monitoring](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/BqDvV/module-review) >> Next step... **Site Reliability Engineering (SRE)**!


=  monitor GCP resources using **StackDriver**:

- **monitoring**,
- **logging**, and
- **diagnostics** for your applications

<img src="../images/StackDriver.png"
        alt="StackDriver.png"
        style="float: left; margin-right: 10px;" />

### StackDriver Overview

([video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/xrHfO/stackdriver-overview))


<img src="../images/StackDriver_overview.png"
        alt="StackDriver_overview.png"
        style="float: left; margin-right: 10px;" />

Multiple integrated products/tasks

<img src="../images/StackDriver_multiple_integrated_products.png"
        alt="StackDriver_multiple_integrated_products.png"
        style="float: left; margin-right: 10px;" />


Integrations partners (security, ...)

<img src="../images/StackDriver_integrations_partners_on_top_of_StackDriver.png"
        alt="StackDriver_integrations_partners_on_top_of_StackDriver.png"
        style="float: left; margin-right: 10px;" />

### Monitoring with StackDriver

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/ra3Di/monitoring)

#### SRE: Site Reliability Engineering

<img src="../images/StackDriver_SRE.png"
        alt="StackDriver_SRE.png"
        style="float: left; margin-right: 10px;" />


<img src="../images/StackDriver_SRE_monitoring.png"
        alt="StackDriver_SRE_monitoring.png"
        style="float: left; margin-right: 10px;" />

<img src="../images/StackDriver_SRE_monitoring_workspace.png"
        alt="StackDriver_SRE_monitoring_workspace.png"
        style="float: left; margin-right: 10px;" />

Alerting policies

<img src="../images/StackDriver_SRE_monitoring_alerts.png"
        alt="StackDriver_SRE_monitoring_alerts.png"
        style="float: left; margin-right: 10px;" />

Best practices for monitoring and alerts:

- **monitor on symptoms**, not necessarily causes. For example, you want to monitor failing queries of a database and then identify whether the database is down.
- **use multiple notification channels**. Like e-mail and SMS. This helps avoid a single point of failure in your alerting strategy.
- **customize your alerts to the audiences need** by describing what actions need to be taken or what resources need to be examined. 
- **avoid noise**, because this will cause alerts to be dismissed overtime. Specifically, adjust monitoring alerts so that they are actionable, and don't just set up alerts on everything possible. 

<img src="../images/StackDriver_SRE_monitoring_alerts_creating_best_practices.png"
        alt="StackDriver_SRE_monitoring_alerts_creating_best_practices.png"
        style="float: left; margin-right: 10px;" />

Uptime checks

Uptime checks can be configured to test the availability of your public services from locations around the world. As you can see on this slide. The type of uptime check can be set to HTTP, HTTPS or TCP. The resource to be checked can be an app engine application, a computer engine instance, a URL of a host, or an AWS instance or Load Balancer. For each uptime check, you can create an alerting policy and view the latency of each global location. 

<img src="../images/StackDriver_SRE_monitoring_alerts_uptime_checks.png"
        alt="StackDriver_SRE_monitoring_alerts_uptime_checks.png"
        style="float: left; margin-right: 10px;" />


Here is an example of an HTTP uptime check. The resources checked every minute with a 10 second timeout. Uptime checks that do not get a response within this timeout period are considered failures. So far there is a 100 percent uptime with no outages. 

<img src="../images/StackDriver_SRE_monitoring_alerts_uptime_check_example.png"
        alt="StackDriver_SRE_monitoring_alerts_uptime_check_example.png"
        style="float: left; margin-right: 10px;" />


If the standard metrics provided by Stackdriver monitoring do not fit your needs, you can create custom metrics.

For example, imagine a game server that has a capacity of 50 users what metric indicator might you use to trigger scaling events. From an infrastructure perspective, you might consider using CPU load, or perhaps network traffic load, as values that are somewhat correlated with the number of users.
But with a custom metric, you could actually pass the current number of users directly from your application into Stackdriver.


<img src="../images/StackDriver_SRE_monitoring_custom_metrics.png"
        alt="StackDriver_SRE_monitoring_custom_metrics.png"
        style="float: left; margin-right: 10px;" />


### Lab. Resource Monitoring with StackDriver

- [video overview](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/IvHOD/lab-intro-resource-monitoring)
- [lab notes](../labs/lab_monitoring_with_StackDriver.md)
- [review of the lab: Resource Monitoring](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/vMsEK/lab-review-resource-monitoring)


### Logging with Stackdriver

- [video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/yXpyQ/logging)

<img src="../images/StackDriver_LOGGING.png"
    alt="StackDriver_LOGGING.png"
    style="float: left; margin-right: 10px;" />

Analyze logs and visualize them wiht **BigQuery** and **Data Studio**

<img src="../images/StackDriver_LOGGING_analysis_with_BigQuery_Studio.png"
    alt="StackDriver_LOGGING_analysis_with_BigQuery_Studio.png"
    style="float: left; margin-right: 10px;" />

How to install Logging agent on VM:

<img src="../images/StackDriver_LOGGING_how_to_install_Logging_agent_on_VM.png"
    alt="StackDriver_LOGGING_how_to_install_Logging_agent_on_VM.png"
    style="float: left; margin-right: 10px;" />

### Error Reporting with Stackdriver

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/J3gb8/error-reporting)

<img src="../images/StackDriver_ERROR_REPORTING.png"
    alt="StackDriver_ERROR_REPORTING.png"
    style="float: left; margin-right: 10px;" />

### Tracing with Stackdriver

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/Whikg/tracing)

<img src="../images/StackDriver_TRACING.png"
    alt="StackDriver_TRACING.png"
    style="float: left; margin-right: 10px;" />

### Debugging with Stackdriver

[video](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/j66MW/debugging)

<img src="../images/StackDriver_DEBUGGER.png"
    alt="StackDriver_DEBUGGER.png"
    style="float: left; margin-right: 10px;" />


### Lab: Error Reporting and Debugging with Stackdriver

- [Lab Intro: Error Reporting and Debugging](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/yLquA/lab-intro-error-reporting-and-debugging)
- [Lab notes](../labs/lab_Stackdriver_error_reporting_debugging.md)
- [Lab Review video: Error Reporting and Debugging](https://www.coursera.org/learn/gcp-infrastructure-core-services/lecture/E00hP/lab-review-error-reporting-and-debugging)



## Resources/Articles


- ["Programmatic Budgets Notification Examples"](https://cloud.google.com/billing/docs/how-to/notify)
- [Export billing to BigQuery](https://cloud.google.com/billing/docs/how-to/export-data-bigquery)
- Free books on Site Reliability Engineering (SRE) (by Google) 
- [GCP metrics](https://cloud.google.com/monitoring/api/metrics_gcp)
- [Stackdriver pricing overview](https://cloud.google.com/stackdriver/pricing#alert-usage)
- [Creating StackDriver custom metrics](https://cloud.google.com/monitoring/custom-metrics/creating-metrics#monitoring-create-metric-python)


# Elastic Cloud Infrastructure: Scaling & Automation


## Content

[2-weeks course intro video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/KHRmh/course-introduction)

* [Interconnecting Networks (Module 1)](#interconnecting-networks-module-1)
    * [Cloud VPN](#cloud-vpn)
    * [lab: Cloud VPN](#lab-cloud-vpn)
    * [Cloud Interconnect &amp; Peering](#cloud-interconnect--peering)
    * [Cloud Interconnect](#cloud-interconnect)
        * [Dedicated Interconnect](#dedicated-interconnect)
    * [Supported Service Providers](#supported-service-providers)
    * [Partner Interconnect](#partner-interconnect)
    * [Comparison of capacity/location's requirements](#comparison-of-capacitylocations-requirements)
    * [Cloud Peering service](#cloud-peering-service)
    * [Direct Peering](#direct-peering)
    * [Carrier Peering](#carrier-peering)
    * [Comparison of Peering options](#comparison-of-peering-options)
    * [Choosing a connection](#choosing-a-connection)
    * [Flow diagram to decide which connection to choose](#flow-diagram-to-decide-which-connection-to-choose)
    * [Sharing VPC Networks: Shared VPC and VPC Peering](#sharing-vpc-networks-shared-vpc-and-vpc-peering)
    * [Shared VPC](#shared-vpc)
    * [VPC Network Peering](#vpc-network-peering)
    * [Comparison Shared VPC vs VPC Peering](#comparison-shared-vpc-vs-vpc-peering)
* [Load Balancing &amp; Autoscaling  (Module 2)](#load-balancing--autoscaling--module-2)
    * [Global load balancers](#global-load-balancers)
    * [Regional load balancers](#regional-load-balancers)
    * [Managed Instance Groups](#managed-instance-groups)
    * [Autoscaling &amp; Health checks](#autoscaling--health-checks)
    * [HTTP(S) Load Balancing](#https-load-balancing)
    * [Lab: Configuring an HTTP Load Balancer with Autoscaling](#lab-configuring-an-http-load-balancer-with-autoscaling)
    * [SSL Proxy/TCP Proxy Load Balancing](#ssl-proxytcp-proxy-load-balancing)
    * [SSL Proxy load balancing](#ssl-proxy-load-balancing)
    * [TCP Proxy load balancing](#tcp-proxy-load-balancing)
    * [Network Load Balancing](#network-load-balancing)
    * [What is a target pooled resource?](#what-is-a-target-pooled-resource)
    * [Internal Load Balancing](#internal-load-balancing)
    * [Lab: Configuring an Internal Load Balancer](#lab-configuring-an-internal-load-balancer)
    * [Choosing a Load Balancer](#choosing-a-load-balancer)
    * [Support for IPV6 is a differentiator](#support-for-ipv6-is-a-differentiator)
    * [Decision tree to help you find your load balancing service](#decision-tree-to-help-you-find-your-load-balancing-service)
* [Infrastructure Automation  (Module 3: Deployment Manager &amp; Terraform)](#infrastructure-automation--module-3-deployment-manager--terraform)
* [Managed Services  (Module 4)](#managed-services--module-4)
* [Resources/Articles](#resourcesarticles)




This course builds on the [Essential Cloud Infrastructure: Core Services](./course_3_Essential_Cloud_Infrastructure__Core_Services.md) course and enhances your study of architecting with Compute Engine.

In this course, we start by going over:

- the different options to interconnect networks to enable you to connect your infrastructure to GCP. 
- GCP’s load balancing and autoscaling services, which you will get to explore directly. 
- the infrastructure automation services like **Deployment Manager** and **Terraform**, so that you can automate the deployment of GCP infrastructure services.
- The other managed services that you might want to leverage in GCP. 






## Interconnecting Networks (Module 1)

- [Module Overview video: Interconnecting Networks](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/Hi6hM/module-overview)
- [Module Review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/BDnmM/module-review)  

= different options to interconnect to GCP

### Cloud VPN

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/oEOJj/cloud-vpn)

<img src="../images/Cloud_VPN.png"
    alt="Cloud_VPN.png"
    style="float: left; margin-right: 10px;" />

Example:

<img src="../images/Cloud_VPN_example.png"
    alt="Cloud_VPN_example.png"
    style="float: left; margin-right: 10px;" />

Dynamic routes with **Cloud Router**

<img src="../images/Cloud_VPN_dynamic_routes_with_Cloud_Router.png"
    alt="Cloud_VPN_dynamic_routes_with_Cloud_Router.png"
    style="float: left; margin-right: 10px;" />

### lab: Cloud VPN

- [Lab Intro: Virtual Private Networks (VPN)](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/Z2dw4/lab-intro-virtual-private-networks-vpn)
- [Lab Review video: Virtual Private Networks (VPN)](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/nTXif/lab-review-virtual-private-networks-vpn)


### Cloud Interconnect & Peering

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/lhPq3/cloud-interconnect-and-peering) 

There are different **Cloud Interconnect** and **Peering services** available to connect your infrastructure to Google's network.

These services can be split into:
- **dedicated connections** versus **shared connections**: Dedicated connections provide a direct connection to Google's network. But, shared connections provide a connection to Google's network through a partner.
- and **layer 2** verses **layer 3** connections: Layer 2 connections use a **VLAN that pipes directly into your GCP environment**, providing connectivity to internal IP addresses in the RFC 1918 address space. Layer 3 connections provide **access to G Suite services, YouTube and Google Cloud APIs using public IP addresses**. 

The services are:

* **Direct Peering**,
* **Carrier Peering**, 
* **Dedicated Interconnect**, 
* and **Partner Interconnect**.

<img src="../images/Cloud_Interconnect_and_Peering.png"
    alt="Cloud_Interconnect_and_Peering.png"
    style="float: left; margin-right: 10px;" />


 Now as I just explained earlier, Google also offers its own Virtual Private Network service called **Cloud VPN**. This service uses the public Internet but traffic is encrypted and provides access to internal IP addresses. That's why Cloud VPN is a useful addition to Direct Peering and Carrier Peering. 


#### Cloud Interconnect

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/OeoTK/cloud-interconnect)

##### Dedicated Interconnect

[Documentation](https://cloud.google.com/interconnect/docs/concepts/dedicated-overview#redundancy)

<img src="../images/Cloud_Interconnect_and_Peering_dedicated_interconnect.png"
    alt="Cloud_Interconnect_and_Peering_dedicated_interconnect.png"
    style="float: left; margin-right: 10px;" />

Definition **SLA***: Service Level Agreement

"99.9% uptime SLA"

**Dedicated Interconnect** needs **Colocation Facility Locations**:

[Documentation on Colocation Facility Locations](https://cloud.google.com/interconnect/docs/concepts/colocation-facilities)

Google locations for physically interconnecting between Google's network and a private network:

<img src="../images/Cloud_Interconnect_physical_Google_location_for_physically_interconnecting_with_private_network.png"
    alt="Cloud_Interconnect_physical_Google_location_for_physically_interconnecting_with_private_network.png"
    style="float: left; margin-right: 10px;" />

#### Supported Service Providers

[Documentation & list of Service providers per country](https://cloud.google.com/interconnect/docs/concepts/service-providers)


#### Partner Interconnect 

If you are no-where near one of this "Colocation Facility Locations", consider **Partner Interconnect**.

[Documentation](https://cloud.google.com/interconnect/docs/concepts/partner-overview#redundancy)

<img src="../images/Cloud_Interconnect_partner_interconnect.png"
    alt="Cloud_Interconnect_partner_interconnect.png"
    style="float: left; margin-right: 10px;" />


#### Comparison of capacity/location's requirements

<img src="../images/Cloud_Interconnect_comparison.png"
    alt="Cloud_Interconnect_comparison.png"
    style="float: left; margin-right: 10px;" />


### Cloud Peering service

- [video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/4QMn8/peering)
- [Documentation on Peering](https://peering.google.com/#/options/peering)
- [Google LLC PeeringDB](https://www.peeringdb.com/asn/15169)
- [Public Peering Exchange Points](https://www.peeringdb.com/net/4319)
- [Peering Service providers](https://cloud.google.com/interconnect/docs/how-to/carrier-peering#service_providers)

There is 2 kinds of Peering:

- Direct Peering 
- Carrier Peering


#### Direct Peering 

<img src="../images/Cloud_Peering_Direct_peering.png"
    alt="Cloud_Peering_Direct_peering.png"
    style="float: left; margin-right: 10px;" />

<img src="../images/Cloud_Peering_Direct_peering_edge_points.png"
    alt="Cloud_Peering_Direct_peering_edge_points.png"
    style="float: left; margin-right: 10px;" />

#### Carrier Peering

If you are no-where near these Google locations, you might consider "**Carrier Peering**".

<img src="../images/Cloud_Peering_Carrier_peering.png"
    alt="Cloud_Peering_Carrier_peering.png"
    style="float: left; margin-right: 10px;" />

#### Comparison of Peering options

<img src="../images/Cloud_Peering_Carrier_comparison_of_options.png"
    alt="Cloud_Peering_Carrier_comparison_of_options.png"
    style="float: left; margin-right: 10px;" />

#### Choosing a connection

The 5 different ways to connect your infrastructure to GCP:

<img src="../images/Cloud_Interconnect_and_Peering.png"
    alt="Cloud_Interconnect_and_Peering.png"
    style="float: left; margin-right: 10px;" />

<img src="../images/Cloud_Interconnect_5_ways.png"
    alt="Cloud_Interconnect_5_ways.png"
    style="float: left; margin-right: 10px;" />


Another way to organize these sources is by:

- **interconnect services**: Interconnect services provide direct access to RFC1918 IP addresses in your VPC with an SLA.
- and by **peering services**: Peering services in contrast offer access to Google public IP addresses only without an SLA. 

 
<img src="../images/Cloud_Peering_Carrier_choose_a_network_connection.png"
    alt="Cloud_Peering_Carrier_choose_a_network_connection.png"
    style="float: left; margin-right: 10px;" />

#### Flow diagram to decide which connection to choose

<img src="../images/Cloud_Interconnect_decision_diagram.png"
    alt="Cloud_Interconnect_decision_diagram.png"
    style="float: left; margin-right: 10px;" />


### Sharing VPC Networks: Shared VPC and VPC Peering

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/d6NEM/shared-vpc-and-vpc-peering)

2 configurations for sharing VPC networks across GCP projects:

- **Shared VPC**: allows you to share a network across several projects in your GCP organization
- **VPC Network Peering**: allows you to configure private communication across projects in same or different organizations.

#### Shared VPC

<img src="../images/Sharing_VPC_networkd_shared_VPC.png"
    alt="Sharing_VPC_networkd_shared_VPC.png"
    style="float: left; margin-right: 10px;" />

#### VPC Network Peering

VPC Network Peering is a decentralized or distributed approach to multiproject networking. Because each VPC network, may remain under the control of separate administrator groups, and maintains its own global firewall, and routing tables.

<img src="../images/Sharing_VPC_networkd_VPC_peering.png"
    alt="Sharing_VPC_networkd_VPC_peering.png"
    style="float: left; margin-right: 10px;" />

#### Comparison Shared VPC vs VPC Peering

<img src="../images/Sharing_VPC_comparison.png"
    alt="Sharing_VPC_comparison.png"
    style="float: left; margin-right: 10px;" />

Differences in Network administration models:

<img src="../images/Sharing_VPC_comparison_network_administration_models.png"
    alt="Sharing_VPC_comparison_network_administration_models.png"
    style="float: left; margin-right: 10px;" />








## Load Balancing & Autoscaling  (Module 2)

- [Module overivew video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/hYGrW/module-overview)
- [Module review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/LNgte/module-review)

Different types of load balancers that can be divided into two categories:

- **global**
- **regional**

<img src="../images/Load_balancing_different_kinds.png"
    alt="Load_balancing_different_kinds.png"
    style="float: left; margin-right: 10px;" />

### Global load balancers

The global load balancers are the HTTP, HTTPS, SSL proxy, and TCP proxy load balancers. 

These load balancers leverage the Google front ends which are software defined, distributed systems that sit in Google's Point-of-Presence and are distributed globally. Therefore, you want to use a global load balancer when your users and instances are globally distributed. Your users need access to the same application and content and you want to provide access using a single anycast IP address.

### Regional load balancers

The regional load balancers are the **internal and network load balancers** and they distribute traffic to instances that are in a single GCP region.

The internal load balancer uses Andromeda which is GCP's software defined network virtualization stack and the network load balancer uses Maglev which is a large distributed software system. There's also another internal load balancer for HTTP, HTTPS traffic, but it's in beta as of this recording

### Managed Instance Groups

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/IbepU/managed-instance-groups)

**Definition**: A managed instance group is a **collection of identical virtual machine instances** that you control as a single entity using an **instance template**.

<img src="../images/Load_balancing_Managed_instances.png"
    alt="Load_balancing_Managed_instances.png"
    style="float: left; margin-right: 10px;" />

You will need to create/use Instance Templates: 

<img src="../images/Load_balancing_instance_template.png"
    alt="Load_balancing_instance_template.png"
    style="float: left; margin-right: 10px;" />

Define "rules" for your instance group:

<img src="../images/Load_balancing_manage_instance_groups.png"
    alt="Load_balancing_manage_instance_groups.png"
    style="float: left; margin-right: 10px;" />

In practice, you are just creating VMs but applying much more rules to that instance group.

#### Autoscaling & Health checks

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/IylfJ/autoscaling-and-health-checks)

Based on utilization and your thresholds:

<img src="../images/Load_balancing_manage_instance_groups_autoscaling.png"
    alt="Load_balancing_manage_instance_groups_autoscaling.png"
    style="float: left; margin-right: 10px;" />

How to decide on a threshold?

<img src="../images/Load_balancing_manage_instance_groups_autoscaling_how_to_set_thresholds.png"
    alt="Load_balancing_manage_instance_groups_autoscaling_how_to_set_thresholds.png"
    style="float: left; margin-right: 10px;" />


Another tool: Health Check, similar to Uptime checks in Stackdriver:

<img src="../images/Load_balancing_manage_instance_groups_autoscaling_create_health_check.png"
    alt="Load_balancing_manage_instance_groups_autoscaling_create_health_check.png"
    style="float: left; margin-right: 10px;" />


### HTTP(S) Load Balancing

[overview video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/suxVg/overview-of-http-s-load-balancing)

<img src="../images/Load_balancing_HTTPS_load_balancing.png"
    alt="Load_balancing_HTTPS_load_balancing.png"
    style="float: left; margin-right: 10px;" />


Architecture of an HTTP(S) load balancer

<img src="../images/Load_balancing_HTTPS_architecture.png"
    alt="Load_balancing_HTTPS_architecture.png"
    style="float: left; margin-right: 10px;" />

Backend services provided by a load balancer:

<img src="../images/Load_balancing_HTTPS_recall_of_services.png"
    alt="Load_balancing_HTTPS_recall_of_services.png"
    style="float: left; margin-right: 10px;" />

Example #1: HTTP load balancer on a single global IP ([video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/RodYr/example-http-load-balancer))

<img src="../images/Load_balancing_example.png"
    alt="Load_balancing_example.png"
    style="float: left; margin-right: 10px;" />


Example #2: HTTP load balancer (Content-based load balancer)

- 2 backends service: WEB (`/<whatever>`) or VIDEO (`/video`) traffic
- traffic is split by the URL header, as specified by the URL map

<img src="../images/Load_balancing_example_2.png"
    alt="Load_balancing_example_2.png"
    style="float: left; margin-right: 10px;" />

HTTPS load balancer ([video](HTTP(S) load balancing))

- same structure as an HTTP load balancer
- SSL certificate
- QUIC transport layer protocol

<img src="../images/Load_balancing_httpS.png"
    alt="Load_balancing_httpS.png"
    style="float: left; margin-right: 10px;" />

SSL certificate:

<img src="../images/Load_balancing_httpS_SSL_certificate.png"
    alt="Load_balancing_httpS_SSL_certificate.png"
    style="float: left; margin-right: 10px;" />



### Lab: Configuring an HTTP Load Balancer with Autoscaling

- [intro video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/WBXBJ/lab-intro-configuring-an-http-load-balancer-with-autoscaling)
- [lab notes](../labs/lab_Load_balancer_with_Autoscaling.md)
- [review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/cF54y/lab-review-configuring-an-http-load-balancer-with-autoscaling)

<img src="../images/lab_Load_balancing_autoscaling.png"
    alt="lab_Load_balancing_autoscaling.png"
    style="float: left; margin-right: 10px;" />

- 2 backends in different regions: us_central_1 & europe_west_1
- demonstrate load balancing
- demonstrate autoscaling




### SSL Proxy/TCP Proxy Load Balancing


#### SSL Proxy load balancing

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/CNZxs/ssl-proxy-load-balancing)

<img src="../images/SSL_proxy.png"
    alt="SSL_proxy.png"
    style="float: left; margin-right: 10px;" />


More on [SSL Proxy Load Balancing Concepts](https://cloud.google.com/load-balancing/docs/ssl/#overview)

Example using SSL Proxy load balancing (recommended over TCP load balancing)

<img src="../images/SSL_proxy_example.png"
    alt="SSL_proxy_example.png"
    style="float: left; margin-right: 10px;" />


#### TCP Proxy load balancing

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/GnrcQ/tcp-proxy-load-balancing)

> NOT ENCRYPTED!!!!

<img src="../images/TCP_proxy.png"
    alt="TCP_proxy.png"
    style="float: left; margin-right: 10px;" />


Example using TCP Proxy load balancing:

<img src="../images/TCP_proxy_example.png"
    alt="TCP_proxy_example.png"
    style="float: left; margin-right: 10px;" />

> Also recommended to use SSL here between the backend and the frontend!

### Network Load Balancing

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/PbNT7/network-load-balancing) 

Network load balancing is a **regional** **non-proxied** load balancing service.

In other words, all traffic is passed through the load balancer instead of being proxied and **traffic can only be balanced between virtual machine instances that are in the same region unlike a global load balancer**.

<img src="../images/network_load_balancer.png"
    alt="network_load_balancer.png"
    style="float: left; margin-right: 10px;" />

**When/Where to use it?**

You can use it to load balance UDP traffic and to load balance TCP NSSL traffic on ports that are not supported by the TCP proxy and SSL proxy load balancer.

The back ends of a network load balancer can be a **template-based instance group** or **target pooled resource**.

#### What is a target pooled resource?

<img src="../images/network_load_balancer_Target_pool_resource.png"
    alt="network_load_balancer_Target_pool_resource.png"
    style="float: left; margin-right: 10px;" />

They have limitations:

<img src="../images/network_load_balancer_Target_pool_resource_limitations.png"
    alt="network_load_balancer_Target_pool_resource_limitations.png"
    style="float: left; margin-right: 10px;" />


### Internal Load Balancing

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/Ys411/internal-load-balancing)

<img src="../images/internal_load_balancer.png"
    alt="internal_load_balancer.png"
    style="float: left; margin-right: 10px;" />

**Internal load balancing** is a **regional**, private load balancing service for TCP and UDP based traffic. 

In other words, this load balancer enables you to run and **scale your services behind a private load balancing IP address**. This means that it is only accessible through the **internal IP address of virtual machine instances that are in the same region**. Therefore, use internal load balancing to configure an internal load balancing IP address, to act as the front end to your private backend instances.


<img src="../images/internal_load_balancer_software_solution.png"
    alt="internal_load_balancer_software_solution.png"
    style="float: left; margin-right: 10px;" />

**"3-tier web service" use case**

<img src="../images/internal_load_balancer_3tier_balancer_use_case.png"
    alt="internal_load_balancer_3tier_balancer_use_case.png"
    style="float: left; margin-right: 10px;" />

### Lab: Configuring an Internal Load Balancer

- [video intro](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/vt2PJ/lab-intro-configuring-an-internal-load-balancer)
- [Lab notes](../labs/lab_Internal_Load_balancer.md) 
- [Lab review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/WPl40/lab-review-configuring-an-internal-load-balancer)

<img src="../images/lab_internal_load_balancer.png"
    alt="lab_internal_load_balancer.png"
    style="float: left; margin-right: 10px;" />


### Choosing a Load Balancer

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/bTKU2/choosing-a-load-balancer)

#### Support for IPV6 is a differentiator

**One differentiator** between the different GCP load balancers is the **support for IPv6 clients**. Only the HTTPS, SSL proxy, and TCP proxy load balancing services support IPV6 clients

<img src="../images/Load_balancing_what_to_choose.png"
    alt="Load_balancing_what_to_choose.png"
    style="float: left; margin-right: 10px;" />

#### Decision tree to help you find your load balancing service

- Global vs regional load balancing,
- external vs internal load balancing,
- and the traffic type

<img src="../images/Load_balancing_decision_tree.png"
    alt="Load_balancing_decision_tree.png"
    style="float: left; margin-right: 10px;" />

<img src="../images/Load_balancing_comparison_table.png"
    alt="Load_balancing_comparison_table.png"
    style="float: left; margin-right: 10px;" />


## Infrastructure Automation  (Module 3: Deployment Manager & Terraform)

- [Module intro video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/v1K52/module-overview)
- [Module review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/uYPYG/module-review)

= "Deployment Manager" or "Terraform" to automate the deployment of **GCP infrastructure Services**

= How to automate the deployment of GCP infrastructure

In this module, we cover :

- how to use **deployment manager** _to automate the deployment of infrastructure_,
- and how to use **GCP marketplace** _to launch infrastructure solutions_.

### Deployment Manager

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/PUEkH/deployment-manager)

Creating resources using GCP:

- GCP Console (GUI, easy for newbies or new to a service)
- Cloud Shell (Command line tool, if you know how to use the service)
- Cloud SDK (programmatically... one step further)

<img src="../images/infrastructure_management_console_cloudshell_deploymentManager.png"
    alt=""
    style="float: left; margin-right: 10px;" />


Deployment Manager takes it one step further: a **declarative approach**.

<img src="../images/infrastructure_management_deploymentManager.png"
    alt="infrastructure_management_deploymentManager.png"
    style="float: left; margin-right: 10px;" />

#### Example: automode network with firewall rule 

<img src="../images/infrastructure_management_deploymentManager_example_network_with_firewall.png"
    alt="infrastructure_management_deploymentManager_example_network_with_firewall.png"
    style="float: left; margin-right: 10px;" />

- automate using templates: one of the automode network, one for the firewall rule.

<img src="../images/infrastructure_management_deploymentManager_example_network_with_firewall_02.png"
    alt="infrastructure_management_deploymentManager_example_network_with_firewall_02.png"
    style="float: left; margin-right: 10px;" />

- [Supported resources type for Deployment Manager](https://cloud.google.com/deployment-manager/docs/configuration/supported-resource-types)


#### Other tools than Deployment Manager

- Terraform
- Ansible
- Packer
- Chef
- puppet
- ...

Many of them works across other Cloud provider, e.g. Terraform!

<img src="../images/infrastructure_management_other_tools_than_deploymentManager.png"
    alt="infrastructure_management_other_tools_than_deploymentManager.png"
    style="float: left; margin-right: 10px;" />

- Other tools similar to Deployment Manager: [Infrastructure as Code (IaC) tools for Google Cloud](https://cloud.google.com/solutions/infrastructure-as-code/#cards)


#### Lab Intro: Automating the Infrastructure of Networks Using Deployment Manager and/or Terraform

- [overview video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/lqJj0/lab-intro-automating-the-infrastructure-of-networks-using-deployment-manager-or)
- [lab notes](../labs/lab_deployment_manager_from_templates_automode_network_with_firewall.md)
- [lab review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/rAynt/lab-review-automating-the-infrastructure-of-networks-using-deployment-manager)


<img src="../images/lab_infrastructure_management_as_code.png"
    alt="lab_infrastructure_management_as_code.png"
    style="float: left; margin-right: 10px;" />

#### Lab: Automating the Infrastructure of networks using Terraform

- [overview video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/lqJj0/lab-intro-automating-the-infrastructure-of-networks-using-deployment-manager-or)
- [lab notes](../labs/lab_deployment_infrastructure_using_Terraform_automode_network_with_firewall.md)
- [lab review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/z1lV3/lab-review-automating-the-infrastructure-of-networks-using-terraform)


### GCP Marketplace

[video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/NUkQL/gcp-marketplace)

<img src="../images/infrastructure_management_GCP_Marketplace.png"
    alt="infrastructure_management_GCP_Marketplace.png"
    style="float: left; margin-right: 10px;" />

GCP marketplace lets you quickly deploy functional software packages that run on GCP. Essentially, GCP marketplace offers production grade solutions from third-party vendors who have already created their own deployment configurations based on Deployment Manager.

[Demo: Launch on GCP Marketplace (LAMP stack)](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/PpU8W/demo-launch-on-gcp-marketplace)


## Managed Services  (Module 4)

- [video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/e9a4x/module-overview)
- [Module review video](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/mS3CY/module-review)

- Other managed services that you would like to leverage in GCP (e.g. MongoDB, Kafka, ...)


As an alternative to infrastructure automation you can eliminate the need to create infrastructure by leveraging a managed service.

Managed services are partial or complete solutions offered as a service. They exist on a continuum between platform as a service and software as a service depending on how much of the internal methods and controls are exposed

 In this module, we give you an overview of **BigQuery**, **Cloud Dataflow**, **Cloud Dataprep** by **Trifecta** and **Cloud Dataproc**. Now, all of these services are for data analytics purposes. And since that's not the focus of this course series, there won't be any labs on this module. Instead we'll have a quick demo to illustrate how easy it is to use managed services.

- [1min about BigQuery](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/1XYDI/bigquery)
   <img src="../images/Managed_Services_BigQuery.png"
    alt="Managed_Services_BigQuery.png"
    style="float: left; margin-right: 10px;" />
   <img src="../images/Managed_Services_BigQuery_02.png"
    alt="Managed_Services_BigQuery_02.png"
    style="float: left; margin-right: 10px;" />

- [1min about Cloud Dataflow](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/k3C1g/cloud-dataflow)
   <img src="../images/Managed_Services_CloudDataflow.png"
    alt="Managed_Services_CloudDataflow.png"
    style="float: left; margin-right: 10px;" />
   <img src="../images/Managed_Services_CloudDataflow_02.png"
    alt="Managed_Services_CloudDataflow_02.png"
    style="float: left; margin-right: 10px;" />

- [1min about Cloud Dataprep](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/ycy9w/cloud-dataprep) by Trifacta
   <img src="../images/Managed_Services_CloudDataPrep.png"
    alt="Managed_Services_CloudDataPrep.png"
    style="float: left; margin-right: 10px;" />
   <img src="../images/Managed_Services_CloudDataPrep_02.png"
    alt="Managed_Services_CloudDataPrep_02.png"
    style="float: left; margin-right: 10px;" />


- [1min about Cloud Dataproc](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/7veQ3/cloud-dataproc)
   <img src="../images/Managed_Services_CloudDataproc.png"
    alt="Managed_Services_CloudDataproc.png"
    style="float: left; margin-right: 10px;" />
   <img src="../images/Managed_Services_CloudDataproc_02.png"
    alt="Managed_Services_CloudDataproc_02.png"
    style="float: left; margin-right: 10px;" />



[Demo: Cloud Dataproc](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation/lecture/6RIEm/demo-cloud-dataproc)


## Resources/Articles


- [Networking in Google Cloud Platform course](https://www.qwiklabs.com/courses/751)
- Load balancing over the QUIC protocol: [QUIC, a multiplexed stream transport over UDP](https://www.chromium.org/quic)
- [SSL Proxy Load Balancing Concepts](https://cloud.google.com/load-balancing/docs/ssl/#overview)
- [Andromeda](https://cloudplatform.googleblog.com/2014/04/enter-andromeda-zone-google-cloud-platforms-latest-networking-stack.html): Google's network virtualization stack, to provide software-defined load balancing that directly delivers the traffic from the client instance to a backend instance. 
- [Supported resources type for Deployment Manager](https://cloud.google.com/deployment-manager/docs/configuration/supported-resource-types)
- Other tools similar to Deployment Manager: [Infrastructure as Code (IaC) tools for Google Cloud](https://cloud.google.com/solutions/infrastructure-as-code/#cards)


# Elastic Cloud Infrastructure: Containers and Services

## Content

* [Course Intro](#course-intro)
* [Module: Application Infrastruture Services Concepts](#module-application-infrastruture-services-concepts)
    * [Cloud Pub/Sub](#cloud-pubsub)
    * [Benefits of Cloud Pub/Sub](#benefits-of-cloud-pubsub)
    * [Basics of Pub/Sub](#basics-of-pubsub)
    * [Complexity handled by Pub/Sub](#complexity-handled-by-pubsub)
    * [Integrations for publishing or subsribing](#integrations-for-publishing-or-subsribing)
    * [Use cases for Pub/Sub](#use-cases-for-pubsub)
    * [API Management](#api-management)
    * [Cloud Endpoints](#cloud-endpoints)
    * [Apigee](#apigee)
    * [Cloud Functions: Serverless offering](#cloud-functions-serverless-offering)
    * [A microservices architecture responding on triggers](#a-microservices-architecture-responding-on-triggers)
    * [Differences Cloud Functions/Endpoints](#differences-cloud-functionsendpoints)
    * [Demo: Cloud Functions](#demo-cloud-functions)
    * [Cloud Source Repositories](#cloud-source-repositories)
    * [Specialty APIs](#specialty-apis)
* [Module: Application Development Services (i.e. App Engine)](#module-application-development-services-ie-app-engine)
    * [App Engine among other compute services](#app-engine-among-other-compute-services)
    * [Example of App Engine app](#example-of-app-engine-app)
    * [Microservices in App Engine](#microservices-in-app-engine)
    * [Choosing Flexible or Standard environment](#choosing-flexible-or-standard-environment)
* [Module: Containers](#module-containers)
    * [Introduction to Containers.](#introduction-to-containers)
    * [Basics of containerization](#basics-of-containerization)
    * [Kubernetes Engine among other compute services](#kubernetes-engine-among-other-compute-services)
    * [History of containerization](#history-of-containerization)
    * [Benefits of containerization](#benefits-of-containerization)
    * [Google Kubernetes Engine](#google-kubernetes-engine)
    * [K8s clusters:](#k8s-clusters)
    * [K8s master endpoint/node:](#k8s-master-endpointnode)
    * [K8s Pods:](#k8s-pods)
    * [K8s Load Balancing using Labels:](#k8s-load-balancing-using-labels)
    * [K8s Deployment:](#k8s-deployment)
    * [K8s Pods scheduled on nodes:](#k8s-pods-scheduled-on-nodes)
    * [K8s deployed with built-in resilience](#k8s-deployed-with-built-in-resilience)
    * [K8s Rolling update:](#k8s-rolling-update)
    * [K8s support for IAM](#k8s-support-for-iam)
    * [K8s multizone container cluster](#k8s-multizone-container-cluster)
    * [K8s Node Pools: instance groups in the k8s cluster](#k8s-node-pools-instance-groups-in-the-k8s-cluster)
    * [K8s more features](#k8s-more-features)
    * [Google Container Registry](#google-container-registry)
    * [Lab: Kubernetes Load Balancing (Overview and Objectives)](#lab-kubernetes-load-balancing-overview-and-objectives)
* [Container environment comparison: Kubernetes Engine, App Engine, or Containers on Compute Engine?](#container-environment-comparison-kubernetes-engine-app-engine-or-containers-on-compute-engine)
* [Resources/Articles](#resourcesarticles)



## Course Intro

- course site: https://www.coursera.org/learn/gcp-infrastructure-containers-services
- [1-week course intro video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/sIb77/elastic-cloud-infrastructure-containers-and-services-course-intro): Elastic Cloud Infrastructure: Containers and Services
- [Course overview video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/OEhAf/module-overview-intro)


**What does "Containers and Services" mean?**

Well, let's start with **containers**. Essentially, containerization is something that Google's been doing for the last 12 years. It's essentially that hybrid between virtual machines and pure Platform as a Service. Now, you can deploy your code in a very nice little package with its dependencies. But the great thing is, it's portable. It can run on-premise, it can run in other cloud providers. Especially, it runs really well in Google Cloud Platform.

So, with containerization in general, we're going to introduce something we call **Kubernetes**, which is essentially **an outsourced version of** the internal system we call **Borg**. Borg essentially finds a home for your containers to live. Kubernetes helps you to automate and orchestrate where your containers live. If you want to take it even further, you can install Kubernetes, you can go to kubernetes.io. It's an open-source project. You can install that on-prem, or other individual cloud providers as well.

We have **a managed service version of that**, and that's called **Google Kubernetes Engine**. So now, we've automated a lot of that infrastructure process, but we've added some additional enhancements. Since Kubernetes has to run anywhere, it can't really integrate as well with native cloud provider features. Now, if you took some of our other courses, you may have learned about autoscaling, our firewall rules, load balancers, et cetera. Google Kubernetes Engine integrates into all those, and so it takes advantage of our global network. It can set up the firewall rules for you, load balancing, autoscaling rules, and you're also doing this with containers. So you really get a huge benefit running on Google Container Engine.

Now, then, **what about our services?** What are they? Well, first of all, they could be the application infrastructure.

- This could be our **Platform as a Service**. These are where you're deploying your own code Java, Python, Go, PHP, you name it.
- Perhaps you want to take advantage of **micro services** so you have **cloud functions**. We also have **Cloud Endpoints**, in which you can publish your APIs. And plus, there's a number of other managed services. Google Cloud Pub/Sub for messaging services between your applications, and thousands of individual APIs that are available to you and your applications, such as Google Maps API, Google Analytics, being able to pull calendar events from Google Calendar and, of course, a number of different cloud APIs, from machine learning APIs, vision APIs, sound, et cetera. You can go ahead and use our API Explorer to find out more, but there's going to be a great deal covered inside of this individual course.


## Module: Application Infrastruture Services Concepts

- [module review video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/L778e/module-1-review-outro)

In this module, you will learn about Cloud Pub/Sub, API Management, Cloud Functions, Cloud Source Repositories, and Specialty APIs.

This module covers **"Application Infrastruture Services Concepts"**:

* Cloud Pub/Sub
* API Management
* Cloud Functions
* Cloud Source Repositories
* Specialty APIs

### Cloud Pub/Sub

[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/oiW44/cloud-pub-sub)



<img src="../images/pubsub.png"
     alt="pubsub.png"
     style="float: left; margin-right: 10px;" />

#### Benefits of Cloud Pub/Sub

<img src="../images/pubsub_benefits.png"
     alt="pubsub_benefits.png"
     style="float: left; margin-right: 10px;" />

#### Basics of Pub/Sub

<img src="../images/pubsub_basics.png"
     alt="pubsub_basics.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/pubsub_basics_multiple_publishers_subscribers.png"
     alt="pubsub_basics_multiple_publishers_subscribers.png"
     style="float: left; margin-right: 10px;" />

#### Complexity handled by Pub/Sub 

<img src="../images/pubsub_basics_complexity.png"
     alt="pubsub_basics_complexity.png"
     style="float: left; margin-right: 10px;" />

#### Integrations for publishing or subsribing

<img src="../images/pubsub_integration_tools.png"
     alt="pubsub_integration_tools.png"
     style="float: left; margin-right: 10px;" />

#### Use cases for Pub/Sub

<img src="../images/pubsub_use_cases.png"
     alt="pubsub_use_cases.png"
     style="float: left; margin-right: 10px;" />


### API Management
 
[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/SA2Uc/api-management)

#### Cloud Endpoints

<img src="../images/API_Management_Cloud_Endpoints.png"
     alt="API_Management_Cloud_Endpoints.png"
     style="float: left; margin-right: 10px;" />

Example: 

<img src="../images/API_Management_Cloud_Endpoints_example.png"
     alt="API_Management_Cloud_Endpoints_example.png"
     style="float: left; margin-right: 10px;" />

#### Apigee

<img src="../images/API_Management_Apigee.png"
     alt="API_Management_Apigee.png"
     style="float: left; margin-right: 10px;" />



### Cloud Functions: Serverless offering

#### A microservices architecture responding on triggers

<img src="../images/Cloud_Functions.png"
     alt="Cloud_Functions.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Cloud_Functions_definition.png"
     alt="Cloud_Functions_definition.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Cloud_Functions_.png"
     alt="Cloud_Functions_.png"
     style="float: left; margin-right: 10px;" />


#### Differences Cloud Functions/Endpoints

1. Endpoint(s)
    - Cloud Enpoints exposes an array of endpoints or API functions.
    - Cloud Functions exposes a **single** endpoint
2. Backend
- Cloud Endpoint backend is an AppEngine backend. So you have a **long running programming environment** with full access to complex data, and storage services
- In Cloud Functions, you have one single piece of code that accepts a limited input, executes **rapidly, produces some output, and then exits**.


<img src="../images/Differences_Cloud_Functions_Cloud_Endpoints.png"
     alt="Differences_Cloud_Functions_Cloud_Endpoints.png"
     style="float: left; margin-right: 10px;" />

#### Demo: Cloud Functions

[demo video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/IR61q/demo-cloud-functions)

1. In CloudShell:

- `npm install --save @google-cloud/storage`
- `mkdir ~/gcf_hello_world`

2. Create `index.js`:

```javascript
exports.helloGET = (req, res) => {
    res.send("Hello World");
}
```

3. Deploy it

`gcloud beta functions deploy helloGET --trigger-http`

4. Use the generated https URL to trigger the function



### Cloud Source Repositories

[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/vvqmA/cloud-source-repositories)


<img src="../images/Cloud_Source_Repositories.png"
     alt="Cloud_Source_Repositories.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Cloud_Source_Repositories_definition.png"
     alt="Cloud_Source_Repositories_definition.png"
     style="float: left; margin-right: 10px;" />
     
### Specialty APIs

<img src="../images/Specialty_APIs_long_list.png"
     alt="Specialty_APIs_long_list.png"
     style="float: left; margin-right: 10px;" />

Example: Cloud ML

<img src="../images/Specialty_APIs_long_list_example_Cloud_ML.png"
     alt="Specialty_APIs_long_list_example_Cloud_ML.png"
     style="float: left; margin-right: 10px;" />


## Module: Application Development Services (i.e. App Engine)

- [Module overivew video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/m1Ra7/module-overview-intro)
- [module review video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/HXCRy/module-2-review-outro)


In this module, we will discuss Google App Engine. App Engine handles all the front end and back end scaling transparently. So all you need to do is focus on the application code.

<img src="../images/AEngine.png"
     alt="AppEngine.png"
     style="float: left; margin-right: 10px;" />

### App Engine among other compute services

[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/GNPSc/app-engine)

<img src="../images/AppEngine_among_other_compute_services.png"
     alt="AppEngine_among_other_compute_services.png"
     style="float: left; margin-right: 10px;" />

### Example of App Engine app

<img src="../images/AppEngine_example_application.png"
     alt="AppEngine_example_application.png"
     style="float: left; margin-right: 10px;" />


### Microservices in App Engine

<img src="../images/AppEngine_microservices.png"
     alt="AppEngine_microservices.png"
     style="float: left; margin-right: 10px;" />

###  Choosing Flexible or Standard environment

<img src="../images/AppEngine_choose_flexible_or_standard.png"
     alt="AppEngine_choose_flexible_or_standard.png"
     style="float: left; margin-right: 10px;" />


## Module: Containers

In this module, you'll be introduced to the concept of containers and you will learn about Google Kubernetes Engine, Google Container Registry, and complete a hands-on lab.

- [module overview video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/WRIMr/module-overview-intro)
- [module review video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/gLy3G/module-3-review)

<a href="https://www.youtube.com/watch?v=4ht22ReBjno" title="The Illustrated Children's Guide to Kubernetes"><img src="../images/k8s_children_book.jpeg" alt="The Illustrated Children's Guide to Kubernetes" /></a>


<a href="https://www.youtube.com/watch?v=O1pv70lPlNc" title="Phippy Goes to the Zoo: A Kubernetes Story - Matt Butcher & Karen Chu"><img src="../images/Phippy-Goes-to-the-Zoo.jpg" alt="Phippy Goes to the Zoo: A Kubernetes Story - Matt Butcher & Karen Chu" /></a>


### Introduction to Containers.

[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/fsoIK/containers)




### Basics of containerization

Google Kubernetes Engine is actually a managed version of Kubernetes,


#### Kubernetes Engine among other compute services

<img src="../images/KubernetesEngine_among_other_compute_services.png"
     alt="KubernetesEngine_among_other_compute_services.png"
     style="float: left; margin-right: 10px;" />

#### History of containerization

<img src="../images/KubernetesEngine_history_of_containarization.png"
     alt="KubernetesEngine_history_of_containarization.png"
     style="float: left; margin-right: 10px;" />

#### Benefits of containerization

<img src="../images/KubernetesEngine_benefits.png"
     alt="KubernetesEngine_benefits.png"
     style="float: left; margin-right: 10px;" />

### Google Kubernetes Engine

[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/jZm1v/kubernetes-engine)

<img src="../images/KubernetesEngine.png"
     alt="KubernetesEngine.png"
     style="float: left; margin-right: 10px;" />


#### K8s clusters:

<img src="../images/KubernetesEngine_how_clusters.png"
     alt="KubernetesEngine_how_clusters.png"
     style="float: left; margin-right: 10px;" />

#### K8s master endpoint/node:

<img src="../images/KubernetesEngine_how_master_endpoint.png"
     alt="KubernetesEngine_how_master_endpoint.png"
     style="float: left; margin-right: 10px;" />

#### K8s Pods:

<img src="../images/KubernetesEngine_how_PODs.png"
     alt="KubernetesEngine_how_PODs.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/KubernetesEngine_how_PODs_share_storage.png"
     alt="KubernetesEngine_how_PODs_share_storage.png"
     style="float: left; margin-right: 10px;" />

#### K8s Load Balancing using Labels:

<img src="../images/KubernetesEngine_how_Load_Balancing_using_labels.png"
     alt="KubernetesEngine_how_Load_Balancing_using_labels.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/KubernetesEngine_how_Load_Balancing_using_labels_example.png"
     alt="KubernetesEngine_how_Load_Balancing_using_labels_example.png"
     style="float: left; margin-right: 10px;" />


#### K8s Deployment: 

<img src="../images/KubernetesEngine_how_Deployment.png"
     alt="KubernetesEngine_how_Deployment.png"
     style="float: left; margin-right: 10px;" />

#### K8s Pods scheduled on nodes:

<img src="../images/KubernetesEngine_how_PODs_Scheduled_on_nodes.png"
     alt="KubernetesEngine_how_PODs_Scheduled_on_nodes.png"
     style="float: left; margin-right: 10px;" />


#### K8s deployed with built-in resilience

<img src="../images/KubernetesEngine_how_resiliency.png"
     alt="KubernetesEngine_how_resiliency.png"
     style="float: left; margin-right: 10px;" />

#### K8s Rolling update:

<img src="../images/KubernetesEngine_how_rolling_update.png"
     alt="KubernetesEngine_how_rolling_update.png"
     style="float: left; margin-right: 10px;" />

#### K8s support for IAM

<img src="../images/KubernetesEngine_how_IAM.png"
     alt="KubernetesEngine_how_IAM.png"
     style="float: left; margin-right: 10px;" />

#### K8s multizone container cluster

<img src="../images/KubernetesEngine_how_multizone_container_cluster.png"
     alt="KubernetesEngine_how_multizone_container_cluster.png"
     style="float: left; margin-right: 10px;" />

#### K8s Node Pools: instance groups in the k8s cluster

<img src="../images/KubernetesEngine_node_pools.png"
     alt="KubernetesEngine_node_pools.png"
     style="float: left; margin-right: 10px;" />


#### K8s more features

<img src="../images/KubernetesEngine_more_features.png"
     alt="KubernetesEngine_more_features.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/KubernetesEngine_more_features_cluster_federation.png"
     alt="KubernetesEngine_more_features_cluster_federation.png"
     style="float: left; margin-right: 10px;" />

### Google Container Registry

[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/IhJnj/container-registry)

Google Container Registry is an open-source Container Management System.

<img src="../images/container_registry.png"
     alt="container_registry.png"
     style="float: left; margin-right: 10px;" />

### Lab: Kubernetes Load Balancing (Overview and Objectives)

- [lab overview video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/xblOd/lab-kubernetes-load-balancing-overview-and-objectives)
- [lab notes: Lab Kubernetes Load Balancing](../labs/Lab_Kubernetes_Load_Balancing.md)
- [lab review video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/tD9bL/lab-kubernetes-load-balancing-review)

<img src="../images/KubernetesEngine_lab.png"
     alt="KubernetesEngine_lab.png"
     style="float: left; margin-right: 10px;" />

In this lab:

- you deployed a container application using Kubernetes and Google Kubernetes Engine.
- Then you tested the configuration of your application.
- You then undeployed it and redeployed it behind a Google Compute Engine HTTP(S) Load Balancer using the Ingress extension to Kubernetes. 


## Container environment comparison: Kubernetes Engine, App Engine, or Containers on Compute Engine?

[video](https://www.coursera.org/learn/gcp-infrastructure-containers-services/lecture/xgKRV/kubernetes-engine-app-engine-or-containers-on-compute-engine)



<img src="../images/containerization_comparison_differentiators.png"
     alt="containerization_comparison_differentiators.png"
     style="float: left; margin-right: 10px;" />
	 
	 
# Reliable Cloud Infrastructure: Design and Process

## Content

* [Detailled Content](#detailled-content)
* [Course Intro](#course-intro)
* [Objectives](#objectives)
* [Modules covered](#modules-covered)
   * [4 parts of this class](#4-parts-of-this-class)
* [Defining the Service](#defining-the-service)
   * [Layered and iterative approach to design used in this training](#layered-and-iterative-approach-to-design-used-in-this-training)
   * [Defining the Service: State and Solution](#defining-the-service-state-and-solution)
   * [Defining the Service: Measurement](#defining-the-service-measurement)
   * [Defining the Service: Gathering Requirements](#defining-the-service-gathering-requirements)
   * [Application: Introducing an example Photo Application service](#application-introducing-an-example-photo-application-service)
   * [Lab: use Deployment Manager to create a VM](#lab-use-deployment-manager-to-create-a-vm)
* [Business-logic Layer design](#business-logic-layer-design)
   * [Business-logic Layer: Design Overview](#business-logic-layer-design-overview)
   * [Business-logic Layer: Microservice Architecture](#business-logic-layer-microservice-architecture)
   * [Application: The photo service is slow!!!](#application-the-photo-service-is-slow)
   * [Design challenge #1: Log aggregation](#design-challenge-1-log-aggregation)
   * [lab: useDeployment Manager: Package and Deploy](#lab-usedeployment-manager-package-and-deploy)
* [Data Layer Design](#data-layer-design)
   * [Classifying and Characterizing Data](#classifying-and-characterizing-data)
   * [Data Ingest and Data Migration](#data-ingest-and-data-migration)
   * [Identification of Storage Needs and Mapping to Storage Systems](#identification-of-storage-needs-and-mapping-to-storage-systems)
   * [Application: The photo service experiences Intermittent Outages](#application-the-photo-service-experiences-intermittent-outages)
   * [Design challenge #2: Complication](#design-challenge-2-complication)
* [Presentation Layer Design](#presentation-layer-design)
   * [Overview](#overview)
   * [Application: Photo service... Periodic Slowdowns](#application-photo-service-periodic-slowdowns)
   * [Design challenge #3: Growth](#design-challenge-3-growth)
   * [lab: Autoscaling](#lab-autoscaling)
* [Resources/Articles](#resourcesarticles)


## Detailled Content

* [Detailled Content](#detailled-content)
* [Course Intro](#course-intro)
* [Objectives](#objectives)
* [Modules covered](#modules-covered)
   * [4 parts of this class](#4-parts-of-this-class)
* [Defining the Service](#defining-the-service)
   * [Layered and iterative approach to design used in this training](#layered-and-iterative-approach-to-design-used-in-this-training)
   * [Defining the Service: State and Solution](#defining-the-service-state-and-solution)
         * [Google's common design](#googles-common-design)
   * [Defining the Service: Measurement](#defining-the-service-measurement)
         * [Service Level Indicators (SLI)](#service-level-indicators-sli)
         * [Service Level Objectives (SLO)](#service-level-objectives-slo)
         * [Service Level Agreements (SLA)](#service-level-agreements-sla)
      * [User Persona](#user-persona)
   * [Defining the Service: Gathering Requirements](#defining-the-service-gathering-requirements)
         * [Just ask questions: who, what...](#just-ask-questions-who-what)
         * [Specify constraints: time, data , users](#specify-constraints-time-data--users)
         * [Scaling requirements: backend, frontend](#scaling-requirements-backend-frontend)
         * [Size requirements](#size-requirements)
   * [Application: Introducing an example Photo Application service](#application-introducing-an-example-photo-application-service)
      * [Gather requirements](#gather-requirements)
      * [Business logic](#business-logic)
      * [From logic, define Services Levels (SLIs, SLOs)](#from-logic-define-services-levels-slis-slos)
      * [Process: test before &amp; during launch](#process-test-before--during-launch)
   * [Lab: use Deployment Manager to create a VM](#lab-use-deployment-manager-to-create-a-vm)
* [Business-logic Layer design](#business-logic-layer-design)
   * [Business-logic Layer: Design Overview](#business-logic-layer-design-overview)
   * [Business-logic Layer: Microservice Architecture](#business-logic-layer-microservice-architecture)
      * [Benefits of microservives](#benefits-of-microservives)
      * [How microservices complicate business logic?](#how-microservices-complicate-business-logic)
      * [When using microservices make sense?](#when-using-microservices-make-sense)
      * [Google's offering for microservices](#googles-offering-for-microservices)
         * [Cloud Functions](#cloud-functions)
         * [Cloud Functions example: translate text in an image](#cloud-functions-example-translate-text-in-an-image)
         * [Cloud Functions example: implementation on GAE &amp; limitations](#cloud-functions-example-implementation-on-gae--limitations)
      * [GCP 12-factor support](#gcp-12-factor-support)
         * [GCP development tools matching 12-factor methodology](#gcp-development-tools-matching-12-factor-methodology)
      * [Mapping computing needs to platform products](#mapping-computing-needs-to-platform-products)
      * [Compute System Provisioning](#compute-system-provisioning)
         * [Prefer &amp; plan for horizontal scaling](#prefer--plan-for-horizontal-scaling)
         * [Pros/Cons of horizontal scaling](#proscons-of-horizontal-scaling)
         * [Horizontal scaling design](#horizontal-scaling-design)
         * [Horizontal scaling tradeoffs: latency, capacity, scalability, cost](#horizontal-scaling-tradeoffs-latency-capacity-scalability-cost)
         * [Design first, dimension later](#design-first-dimension-later)
   * [Application: The photo service is slow!!!](#application-the-photo-service-is-slow)
      * [Business problem](#business-problem)
      * [Systematic logical troubleshooting](#systematic-logical-troubleshooting)
      * [Collaboration &amp; communication](#collaboration--communication)
      * [Break down business logic on the photo service](#break-down-business-logic-on-the-photo-service)
      * [Identify the attributes of the different services?](#identify-the-attributes-of-the-different-services)
      * [Segregate services for better performance and scalability](#segregate-services-for-better-performance-and-scalability)
      * [What about our Service Level Objectives (SLOs) and Indicators (SLIs)](#what-about-our-service-level-objectives-slos-and-indicators-slis)
   * [Design challenge #1: Log aggregation](#design-challenge-1-log-aggregation)
   * [lab: useDeployment Manager: Package and Deploy](#lab-usedeployment-manager-package-and-deploy)
* [Data Layer Design](#data-layer-design)
   * [Classifying and Characterizing Data](#classifying-and-characterizing-data)
      * [BASE](#base)
      * [ACID](#acid)
      * [What are the data consistency requirements?](#what-are-the-data-consistency-requirements)
      * [What are you truing to optimize? Domain/App specific](#what-are-you-truing-to-optimize-domainapp-specific)
   * [Data Ingest and Data Migration](#data-ingest-and-data-migration)
      * [GCS migration tools: console, gsutil, JSON API](#gcs-migration-tools-console-gsutil-json-api)
      * [GCS migration tools for large transfers: Cloud Storage Transfer Service](#gcs-migration-tools-for-large-transfers-cloud-storage-transfer-service)
      * [GCS migration tools for large transfers without network: Google Transfer Appliance](#gcs-migration-tools-for-large-transfers-without-network-google-transfer-appliance)
      * [GCS migration tools scal-up table](#gcs-migration-tools-scal-up-table)
      * [Data ingestion tools](#data-ingestion-tools)
   * [Identification of Storage Needs and Mapping to Storage Systems](#identification-of-storage-needs-and-mapping-to-storage-systems)
      * [Choose a storage solution between: DISK, MOBILE or CLOUD solutions](#choose-a-storage-solution-between-disk-mobile-or-cloud-solutions)
      * [Choose a storage solution for unstructured data on Cloud Storage: regional, multi-regional, nearline, coldline](#choose-a-storage-solution-for-unstructured-data-on-cloud-storage-regional-multi-regional-nearline-coldline)
      * [Choose a storage solution for analytics: BigQuery](#choose-a-storage-solution-for-analytics-bigquery)
      * [Choose a storage solution for SQL (scalable or not): Clud SQL or Spanner](#choose-a-storage-solution-for-sql-scalable-or-not-clud-sql-or-spanner)
      * [Choose a storage solution for NoSQL: Cloud Datastore](#choose-a-storage-solution-for-nosql-cloud-datastore)
      * [Choose a storage solution: decision tree &amp; summary table](#choose-a-storage-solution-decision-tree--summary-table)
   * [Application: The photo service experiences Intermittent Outages](#application-the-photo-service-experiences-intermittent-outages)
      * [Business problem](#business-problem-1)
      * [Systematic logical troubleshooting](#systematic-logical-troubleshooting-1)
      * [Break down business logic on the photo service](#break-down-business-logic-on-the-photo-service-1)
      * [New Service Level Objectives (SLOs) and Indicators (SLIs)](#new-service-level-objectives-slos-and-indicators-slis)
   * [Design challenge #2: Complication](#design-challenge-2-complication)
* [Presentation Layer Design](#presentation-layer-design)
   * [Overview](#overview)
      * [Network Configuration](#network-configuration)
         * [Impact of Location](#impact-of-location)
         * [Impact of Load Balancing](#impact-of-load-balancing)
         * [Choosing your type of load balancer](#choosing-your-type-of-load-balancer)
      * [Integration with other Environments](#integration-with-other-environments)
         * [Network edge configuration for users and clients](#network-edge-configuration-for-users-and-clients)
         * [Network connections to other networks (e.g. data center, another cloud)](#network-connections-to-other-networks-eg-data-center-another-cloud)
            * [Dedicated interconnects](#dedicated-interconnects)
            * [VPN configurations](#vpn-configurations)
   * [Application: Photo service... Periodic Slowdowns](#application-photo-service-periodic-slowdowns)
      * [Business problem](#business-problem-2)
      * [Systematic logical troubleshooting](#systematic-logical-troubleshooting-2)
      * [Collaboration &amp; communication: Report, Document, build policy](#collaboration--communication-report-document-build-policy)
      * [Break down business logic on the photo service](#break-down-business-logic-on-the-photo-service-2)
      * [What about our Service Level Objectives (SLOs) and Indicators (SLIs)](#what-about-our-service-level-objectives-slos-and-indicators-slis-1)
   * [Design challenge #3: Growth](#design-challenge-3-growth)
   * [lab: Autoscaling](#lab-autoscaling)
* [Resources/Articles](#resourcesarticles)



## Course Intro

- course site: https://www.coursera.org/learn/cloud-infrastructure-design-process
- [2-weeks course intro video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/Gdkgd): Architecting with Google Cloud Platform Design and Process class
- [Course overview video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/Cp9Nv/course-overview)


While researching the materials for this class, we learned that expert cloud architects often use complex assemblies in their solutions. The assembly changes many aspects of the design at once, and it's very hard to learn design skills from these complex examples.

**A good analogy is an expert chef**.

The chef is preparing a dish and adds a bowl of something, you ask what it is and the chef responds, "Well, that's just a half dozen herbs and spices I like to use." You can't duplicate the recipe if you don't know what the ingredients are in their proportions. So in this class, we've broken down the process of the experts into clear understandable steps. We've tried to show all the ingredients.

The class uses a **tiered design model to organize the learning**. And along the way, you'll have the opportunity to apply what you learned to example designs. 

Speaking of examples, the example solutions in the class exercises are intended to get you thinking about **design**. There are adequate solutions but not perfect solutions, you'll probably think of ways to improve on these solutions and come up with your own designs that are better and that's exactly what we want you to do, to learn to develop your own designs.

<img src="../images/design_and_process.png"
     alt="design_and_process.png"
     style="float: left; margin-right: 10px;" />


## Objectives

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/Cp9Nv/course-overview)


- GCP design skills
- Process knowledge and skills
- Prepare you to continue learning by exposing you to concepts and models (differents SRE & best practices)
- Introduce Deployment Manager as a Cloud Architect tool (template & design)


Learned in the labs:

<img src="../images/course_6_design_and_process_list_labs.png"
     alt="course_6_design_and_process_list_labs.png"
     style="float: left; margin-right: 10px;" />


## Modules covered

1. **Defining the service** (What is that exact process?)
2. **Business logic layer design** (This can also be done on paper before deploying resources)
3. **Data layer design** (identify the data layer, help identify which services we may utilize)
4. **Presentation layer design** (identify the presentation layer, help identify which services we may utilize)
5. **Design for resiliency, scalability and Disaster recovery (DR)** (Build it stronger)
6. **Design for security** (Build it stronger)
7. **Capacity planning and cost optimization** (How much will this design cost? Help design an acceptable budget)
8. **Deployment, monitoring and alerting, and incident response** (Key if you have/want an automated deployment, to understand how we respond to incidences)


### 4 parts of this class

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/SIBjx/modules-in-this-course)

1. Introduction to **architecting concepts and principles**.
   * Defining the Service

2. The application of those principles to a **real world design**.
   
   You'll begin with an application on a single virtual machine, and through the modules, you'll evolve the design into a sophisticated scalable, resilient, stable, secure solution.
3. A **related application problem**.

   You'll be presented with the problem and challenge to come up with your own design, to think through the design challenge on your own, after, you can compare your design to a standard solution. 
4. Hands on labs with **Google Deployment Manager**.

   Deployment Manager is a template-based infrastructure tool. It enables you to produce identical environments for development, test in production, and it's useful for documenting and testing variations in your designs. So you'll be learning deployment manager as a cloud architect tool.


## Defining the Service

- [video course overview](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/hRsj7/defining-the-service-course-overview)

A step-by-step process so you can learn how to think about cloud design.

### Layered and iterative approach to design used in this training

- [video "Define the Service" process](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/VGUfp/defining-the-service-module-overview)

Each module expands on the previous design, exploring it from a new perspective, evolving it into a scalable, reliable, stable, secure design


After introducing a layered model, the module discusses three concepts that are critical to design and to cloud architecture. These are:

- state,
- measurement,
- and requirements.

<img src="../images/Design_process_rough_design.png"
     alt="Design_process_rough_design.png"
     style="float: left; margin-right: 10px;" />

1. **Design the service... roughly** (we will iterate on it) and involve the team going through that design process.
2. then continue with a **more structured design approach**... iterate!

   - is it handling different scenarios?
   - do we have the proper budget?
   - ...
3. Define measurable
   
   - define measurable instruments that will allow us to define
   - are we succeeding the goals that we've set out?
   - What are exactly our service level objectives?
   - and how do we create service level indicators to measure those?
4. Then we move to our **three-tier architecture**:

    - Presentation layer (Networking)
    - Business logic layer (Compute)
    - Data layer (Storage)

    <img src="../images/Design_process_3-tier_architecture.png"
        alt="Design_process_3-tier_architecture.png"
        style="float: left; margin-right: 10px;" />

5. Resiliency, scalability and disaster recovery

    <img src="../images/Design_process_understand_disaster_resiliency.png"
        alt="Design_process_understand_disaster_resiliency.png"
        style="float: left; margin-right: 10px;" />

6. Security

    <img src="../images/Design_process_security.png"
        alt="Design_process_security.png"
        style="float: left; margin-right: 10px;" />

7. Budget, Capacity planning and cost optimization

    <img src="../images/Design_process_budget.png"
        alt="Design_process_budget.png"
        style="float: left; margin-right: 10px;" />

8. Deployment, monitoring, alerting and incident response

    <img src="../images/Design_process_deployment_types.png"
        alt="Design_process_deployment_types.png"
        style="float: left; margin-right: 10px;" />


**Recency bias**

(always remember to try new instead of re-using old)

<img src="../images/Design_process_Recency_assess.png"
     alt="Design_process_Recency_assess.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Design_process_summary.png"
     alt="Design_process_summary.png"
     style="float: left; margin-right: 10px;" />


### Defining the Service: State and Solution


[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/6aTsE/defining-the-service-state-and-solution) 

State refers to **any action in the system that depends on the memory of a preceding action**. And the data that must be remembered is called state information.

For example, compare two sets of directions:

1. The first one says, walk south for one block and take the first right.
2. The second one says, turn right one block after you've passed the market.

The second instruction requires you to remember that you've passed the market, so it's **stateful**. Whereas the first one does not require you to remember anything, so it's **stateless**. Whether a system is stateful or stateless has a lot of influence on design. And in particular, you have to decide where to store state information, how to retrieve it, and what to do if it's lost.

<img src="../images/Design_process_statefull_stateless.png"
     alt="Design_process_statefull_stateless.png"
     style="float: left; margin-right: 10px;" />

Analogy with kitchen:

- you could build everything yourself (the protein, the vegetables, make the sauce, ...). That gives you **more control** by centralizing everything and allow you to forsee the problem before it gets to the end state. **Problem is scaling**.
- in a stateless approach, it's easier to handle scaling and distribution.

<img src="../images/Design_process_statefull_stateless_cook_analogy.png"
     alt="Design_process_statefull_stateless_cook_analogy.png"
     style="float: left; margin-right: 10px;" />


So what are your states? What kind of information should be stored? Where can we store them? How can we manage them?

Best state is **NO states**. 

<img src="../images/Design_process_where_storing_information.png"
     alt="Design_process_where_storing_information.png"
     style="float: left; margin-right: 10px;" />

How do dal with states?

<img src="../images/Design_process_deal_with_states.png"
     alt="Design_process_deal_with_states.png"
     style="float: left; margin-right: 10px;" />

**Avoid hotspots**. Instead, push them to a backend.

<img src="../images/Design_process_states_Avoid_hotpsots.png"
     alt="Design_process_states_Avoid_hotpsots.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Design_process_states_Avoid_hotpsots_push_to_backend.png"
     alt="Design_process_states_Avoid_hotpsots_push_to_backend.png"
     style="float: left; margin-right: 10px;" />

You could use **cache**, but that might become overloaded, so to overcome that,  distribute the states onto several backend with load-balancing.

<img src="../images/Design_process_states_distribute_backend_instead_of_cache.png"
     alt="Design_process_states_distribute_backend_instead_of_cache.png"
     style="float: left; margin-right: 10px;" />


##### Google's common design

This solution is a design process and fits many solutions:

Frontend:

- Cloud DNS
- HTTPS Load balancer before pre-emptible machines and store states in the backend.

Backend:
- backend also stateless, also made of pre-emptible machines, pushing data to "a static **stateful** cluster". This stateful cluster is charted, replicated.


<img src="../images/Design_process_states_design_fitting_many_solutions.png"
     alt="Design_process_states_design_fitting_many_solutions.png"
     style="float: left; margin-right: 10px;" />

### Defining the Service: Measurement

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/qhave/defining-the-service-measurement)


Measurement is the key to creating a stable and manageable system.

The Cloud Architect doesn't just design and implement a solution. There are usually required to stick around for some time after the implementation to stabilize the system and make sure it can be operated and maintained. If you design from the beginning, identifying **indicators to be measured** and **objectives to compare them against**, you'll have the information needed for the stabilization processes that surround the system. 

How you should measure your service and discuss the terms we use to describe those measurements?

As the designer of your service, it's up to you to define **how your service should look and feel to your users**. It's equally important **to establish metrics that tell your users what they can expect from your service in terms of reliability and performance**. We'll call this the service level

<img src="../images/Design_process_Service_level.png"
     alt="Design_process_Service_level.png"
     style="float: left; margin-right: 10px;" />

To define a service level, you need to identify what the users care about.

1. **Service Level Indicators (SLI)**: Our first step is to identify the Service Level Indicators or SLIs.
    For example, the availability of a web page or how fast the system responds when a user clicks a button.
2. **Service Level Objectives (SLO)**: Next, we determined the threshold of pain for each of these SLIs. Meaning at what point the users will decide that the service is working properly.
    We'll call this the Service Level Objective or SLO.
3. **Service Level Agreements (SLA)**: Finally, some services are so critical that a formal business agreement will exist between the provider and the users to guarantee a specific behavior and to compensate the users if the service fails to meet this expectation.

<img src="../images/Design_process_Service_level_agreements.png"
     alt="Design_process_Service_level_agreements.png"
     style="float: left; margin-right: 10px;" />

Chances are that you've seen terms like Service Level Agreement or SLA. Perhaps you've even wonder how these figures are determined or more importantly, how they're monitored. Service levels define how a given service or product should behave. There are a number of factors that go into service levels ranging from availability specifications such as 99.99 percent up time or performance specification such as a minimum response time of one second. Service levels helps set the user's expectation and help keep their expectations in line with the design of the service.

##### Service Level Indicators (SLI)

 SLIs should be directly observable and measurable by the users. SLIs should not be internal system metrics such as server, CPU utilization or the number of server failures. This is done for two reasons:
 1. the user can't directly measure those internal factors because they are on the outside of the system.
 2. utilization isn't really an effective measure of the the usability of a system. Instead, utilization is a metric best used by auto-scalars to maintain a consistent user experience

<img src="../images/Design_process_Example_SLI.png"
     alt="Design_process_Example_SLI.png"
     style="float: left; margin-right: 10px;" />

Example SLI:
- users know the service **functions well** because they do not receive errors
- they know it **performs well** because the latency between services is very quick
- they have no idea of the load of CPUs, and they don't care!


<img src="../images/Design_process_Example_SLI_example.png"
     alt="Design_process_Example_SLI_example.png"
     style="float: left; margin-right: 10px;" />


 To provide an accurate measurement of the latency a user would experience, we need to monitor additional systems. In this case, we need to know the true latency of our application. We must account for the latency of a load balancer and of the data server. Note that in this case, we don't have visibility to the user's Internet connection. So, our SLI will be the end-to-end latency from the front-end web load balancer through our service and then back to the data server

<img src="../images/Design_process_Example_SLI_additional_metrics.png"
     alt="Design_process_Example_SLI_additional_metrics.png"
     style="float: left; margin-right: 10px;" />


##### Service Level Objectives (SLO)

Once we've identified what the users care about, we need to quantify those thresholds of pain. This is represented as the Service Level Objective or SLO. The SLO is a threshold value for an SLI, and the result should be set at the lowest or poorest level of service, where the users will still consider the service to be in good working order. That's to say, the SLO represents the point at which the user would consider opening a support ticket because the service failed to meet his or her expectation.


<img src="../images/Design_process_Example_SLO.png"
     alt="Design_process_Example_SLO.png"
     style="float: left; margin-right: 10px;" />

Determining an SLO:

<img src="../images/Design_process_Determining_SLO.png"
     alt="Design_process_Determining_SLO.png"
     style="float: left; margin-right: 10px;" />


When designing your SLOs, it's important to **put reality above utopia**. While we'd love to have a service that is up 100 percent of the time, that also means that the service can never be updated. Google has adopted an error budget methodology. Instead of assuming that every service will run perfectly, services are given error budgets for the SLOs that operates a bit like spending money. Each service starts with a set amount of errors that are considered normal and expected. Any errors in excess of this budget are considered outages. So, the goal is to perform all the system maintenance and updates within this budget. As the days go by each month, the error budget is replenished, giving the development and operations team the breathing room needed to implement changes and apply updates.

<img src="../images/Design_process_Reality_in_service_levels.png"
     alt="Design_process_Reality_in_service_levels.png"
     style="float: left; margin-right: 10px;" />

 it's important to ensure that all SLOs are based on the user experience, rather than an internal system metric. For example, if a service becomes unavailable at 03:00 AM, but no one notices, perhaps the SLO shouldn't be based on a 24-hour day. 

<img src="../images/Design_process_Determining_SLO_alerts_on_UX.png"
     alt="Design_process_Determining_SLO_alerts_on_UX.png"
     style="float: left; margin-right: 10px;" />

##### Service Level Agreements (SLA)

Going one step further, we have SLAs. As previously mentioned, some services are so critical that the loss of the service could represent loss of money for the customer or even loss of life in extreme situations such as, autonomous cars or air traffic control. These contracts define an even more restrictive level of service that is lower or poorer than what is defined in the SLO. The key difference here is that the SLO is a soft target used by the owner of the service to set expectations. The SLA is a business contract that grants a user compensation if the service falls below a certain threshold. Therefore, developers and operations team strive to maintain the SLO, which inherently meets the SLA figures.

<img src="../images/Design_process_Example_SLI_SLO_SLA.png"
     alt="Design_process_Example_SLI_SLO_SLA.png"
     style="float: left; margin-right: 10px;" />


An SLA is not the minimum point at which a services is considered usable. There are some services that are so mission-critical, that the service provider must provide a written guarantee, that the service will perform above a certain specification. That specification is the SLA, and breaking the SLA grants compensation from the provider to the users. Keep in mind, not all services have SLAs, but all services should have an SLO. It's also possible that providers might not publicly disclose their SLOs for fear that users might incorrectly associate the SLO with an SLA.

<img src="../images/Design_process_Example_SLA.png"
     alt="Design_process_Example_SLA.png"
     style="float: left; margin-right: 10px;" />


#### User Persona

If you don't know your user, how can you establish what they find important and acceptable? The answer comes from marketing concept used when developing user interfaces. The user persona. A user persona is an abstract representation of how a certain set of users will use your service. For instance, the power user, the casual user, the road where you are in, the inpatient user. User personas can help you determine the SLIs and the SLOs for your service by understanding how each group will actually use your service.

<img src="../images/Design_process_User_persona.png"
     alt="Design_process_User_persona.png"
     style="float: left; margin-right: 10px;" />


### Defining the Service: Gathering Requirements

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/iHvCE/defining-the-service-gathering-requirements)

Requirements or items that are important to the business, business goals. Requirements are related to measurement. For example; one requirement might be that the service is responsive to users. That requirement is embodied in an objective, such as; no more than half second latency in responding to customer request. And the objective is supported by a measurable indicator, such as; measuring round trip time between user request and delivery of a result. This lesson covers gathering requirements and things to consider and discuss that will help identify requirements. 

##### Just ask questions: who, what...
> 
> * Who's the main character?
> * What do they do?
> * What do they look like?
> * Are they old?
> * Do they have problems?
> * ... 

<img src="../images/Design_process_questions_for_gathering_requirements.png"
     alt="Design_process_questions_for_gathering_requirements.png"
     style="float: left; margin-right: 10px;" />

##### Specify constraints: time, data , users
     
<img src="../images/Design_process_questions_for_time_data.png"
     alt="Design_process_questions_for_time_data.png"
     style="float: left; margin-right: 10px;" />

##### Scaling requirements: backend, frontend

<img src="../images/Design_process_questions_scaling_requirements.png"
     alt="Design_process_questions_scaling_requirements.png"
     style="float: left; margin-right: 10px;" />

##### Size requirements

<img src="../images/Design_process_questions_size_requirements.png"
     alt="Design_process_questions_size_requirements.png"
     style="float: left; margin-right: 10px;" />

This can limit your choice in the type of tools, implementation you will have to build.

### Application: Introducing an example Photo Application service

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/YvgUm/introducing-an-example-photo-application-service)

This lesson introduces the Thumbnail photo service, an example application, that will evolve and design throughout the class. This lesson focuses on applying the principles that were learned in the previous lessons in this module. In this case, we're going to introduce a very basic photo service.

<img src="../images/app_photo_service.png"
     alt="app_photo_service.png"
     style="float: left; margin-right: 10px;" />

#### Gather requirements

* users
* speed
* resources
* scale
* size
* availability

<img src="../images/app_photo_service_gather_requirements.png"
     alt="app_photo_service_gather_requirements.png"
     style="float: left; margin-right: 10px;" />

#### Business logic

<img src="../images/app_photo_service_gather_busines_logic.png"
     alt="app_photo_service_gather_busines_logic.png"
     style="float: left; margin-right: 10px;" />

#### From logic, define Services Levels (SLIs, SLOs)

<img src="../images/app_photo_service_SLO.png"
     alt="app_photo_service_SLO.png"
     style="float: left; margin-right: 10px;" />

#### Process: test before & during launch

<img src="../images/app_photo_service_tests.png"
     alt="app_photo_service_tests.png"
     style="float: left; margin-right: 10px;" />

Pre-production tests:

* unit tests
* integration tests
* system tests
* stress test

Production tests:

* Rollout (staged) with user
* acceptance, A/B testing


### Lab: use Deployment Manager to create a VM

- [video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/XjMe5/lab-intro-deployment-manager)

- understand YAML templates syntax
- deploy a single appserver with Deployment Manager




## Business-logic Layer design

### Business-logic Layer: Design Overview

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/tVAxY/business-logic-layer-design-overview)

**What is business logic?**

In computer science, it's **the code that implements business rules that determines what happens to data**. In other words, **processing**. I think of business logic in this way.

Consider the transaction of buying an airline ticket. I could buy the ticket at the counter. I could buy the ticket through a travel agent. I could buy the ticket from a kiosk machine at the airport. I could buy the ticket online using a web browser, or I could buy the ticket using an app on my phone. All of these are different front ends or interfaces, but the transaction itself, of purchasing the ticket, remains the same no matter what interface is used. And that, to me, is the business logic. By definition, business logic operates on data. And that means executing code, processing. So for this reason, the business logic layer is also the part of the design process where you'll consider cloud processing options and determine what service the business logic code will use when it needs to run.

**Microservices** are **a specific kind of Service Oriented Architecture**, or **SOA**, that leverages small, stateless processing for improved scalability and resiliency.

Microservices design is a popular approach to applications, and this lesson explores how microservices work and support on the Google Cloud platform for microservices.


In computer software, business logic or domain logic is part of the program that encodes the real-world business rules that determine how data can be created, stored, and changed. 

In this module, we're going to cover:

* **microservice architecture**,
* **how GCP supports 12-factor**,
* **mapping computing needs to platform products**,
* **compute system provisioning**.

We're also going to explore our photo service. We're going to have our first issue. The photo service is slow, so we're going to have to identify what the cause is, and then understand exactly how we're going to redesign for this. We're also going to have a new design challenge, and this is going to have to do with our log aggregation which you're going to see as a result of our photo service. This will be followed up by another lab. This will be our GCP lab deployment manager in package and deploy.

So now we're going to **package**:

* learn how to package our applications
* and deploy those versus just simply deploying applications in their source.

### Business-logic Layer: Microservice Architecture

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/mLIMB/business-logic-layer-microservice-architecture)

Microservices are a specific kind of service-oriented architecture or SOA that leverages small, stateless processing from proof scalability and resiliency.

Microservices design is a popular approach to applications and this lesson explores how microservices work and support on the Google Cloud Platform for microservices.


<img src="../images/Design_process_business_logic_microservices.png"
     alt="Design_process_business_logic_microservices.png"
     style="float: left; margin-right: 10px;" />

#### Benefits of microservives

<img src="../images/Design_process_business_logic_microservices_benefits_drawbacks.png"
     alt="Design_process_business_logic_microservices_benefits_drawbacks.png"
     style="float: left; margin-right: 10px;" />

#### How microservices complicate business logic?

<img src="../images/Design_process_business_logic_microservices_how_much_more_complex.png"
     alt="Design_process_business_logic_microservices_how_much_more_complex.png"
     style="float: left; margin-right: 10px;" />

#### When using microservices make sense?

<img src="../images/Design_process_business_logic_microservices_use_when_make_sense.png"
     alt="Design_process_business_logic_microservices_use_when_make_sense.png"
     style="float: left; margin-right: 10px;" />

#### Google's offering for microservices

##### Cloud Functions

<img src="../images/Design_process_business_logic_microservices_cloud_functions.png"
     alt="Design_process_business_logic_microservices_cloud_functions.png"
     style="float: left; margin-right: 10px;" />


##### Cloud Functions example: translate text in an image

<img src="../images/Design_process_business_logic_microservices_cloud_functions_example.png"
     alt="Design_process_business_logic_microservices_cloud_functions_example.png"
     style="float: left; margin-right: 10px;" />

##### Cloud Functions example: implementation on GAE & limitations

<img src="../images/Design_process_business_logic_microservices_cloud_functions_example_in_GAE.png"
     alt="Design_process_business_logic_microservices_cloud_functions_example_in_GAE.png"
     style="float: left; margin-right: 10px;" />

#### GCP 12-factor support

https://12factor.net/

<img src="../images/Design_process_12-factor.png"
     alt="Design_process_12-factor.png"
     style="float: left; margin-right: 10px;" />

##### GCP development tools matching 12-factor methodology

<img src="../images/Design_process_12-factor_GCP_tools.png"
     alt="Design_process_12-factor_GCP_tools.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Design_process_12-factor_GCP_tools_2.png"
     alt="Design_process_12-factor_GCP_tools_2.png"
     style="float: left; margin-right: 10px;" />

Storing states in your environment

<img src="../images/Design_process_12-factor_GCP_tools_storing_states.png"
     alt="Design_process_12-factor_GCP_tools_storing_states.png"
     style="float: left; margin-right: 10px;" />

#### Mapping computing needs to platform products

<img src="../images/Design_process_12-factor_where_to_get_CPUs.png"
     alt="Design_process_12-factor_where_to_get_CPUs.png"
     style="float: left; margin-right: 10px;" />

Think of **App Engine** first, then **K8s** if you need more control on the scaling, or **Compute Engine** as a last resort.

<img src="../images/Design_process_12-factor_think_about_appengine_first.png"
     alt="Design_process_12-factor_think_about_appengine_first.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Design_process_12-factor_think_about_appengine_code_first.png"
     alt="Design_process_12-factor_think_about_appengine_code_first.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Design_process_12-factor_think_about_k8s_second.png"
     alt="Design_process_12-factor_think_about_k8s_second.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Design_process_12-factor_think_about_ComputeEngine_third.png"
     alt="Design_process_12-factor_think_about_ComputeEngine_third.png"
     style="float: left; margin-right: 10px;" />


#### Compute System Provisioning

<img src="../images/Design_process_compute_system_provisioning.png"
     alt="Design_process_compute_system_provisioning.png"
     style="float: left; margin-right: 10px;" />

##### Prefer & plan for horizontal scaling

<img src="../images/Design_process_compute_system_provisioning_how_to_grow.png"
     alt="Design_process_compute_system_provisioning_how_to_grow.png"
     style="float: left; margin-right: 10px;" />

##### Pros/Cons of horizontal scaling

<img src="../images/Design_process_compute_system_provisioning_prefer_horizontal_scaling.png"
     alt="Design_process_compute_system_provisioning_prefer_horizontal_scaling.png"
     style="float: left; margin-right: 10px;" />

##### Horizontal scaling design

<img src="../images/Design_process_compute_system_provisioning_horizontal_scaling_design.png"
     alt="Design_process_compute_system_provisioning_horizontal_scaling_design.png"
     style="float: left; margin-right: 10px;" />


##### Horizontal scaling tradeoffs: latency, capacity, scalability, cost

<img src="../images/Design_process_compute_system_provisioning_horizontal_scaling_tradeoffs.png"
     alt="Design_process_compute_system_provisioning_horizontal_scaling_tradeoffs.png"
     style="float: left; margin-right: 10px;" />

##### Design first, dimension later

<img src="../images/Design_process_compute_system_provisioning_design_first_dimension_later.png"
     alt="Design_process_compute_system_provisioning_design_first_dimension_later.png"
     style="float: left; margin-right: 10px;" />


### Application: The photo service is slow!!!

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/rb6kW/the-photo-service-is-slow)

#### Business problem

- the service has been slowing down
- what's te cause of this slow service?
- What can be done about it?
- What opportunities does this offer for improving the design?


<img src="../images/app_photo_service_slow.png"
     alt="app_photo_service_slow.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/app_photo_service_problem.png"
     alt="app_photo_service_problem.png"
     style="float: left; margin-right: 10px;" />

#### Systematic logical troubleshooting

<img src="../images/app_photo_service_problem_troubleshooting.png"
     alt="app_photo_service_problem_troubleshooting.png"
     style="float: left; margin-right: 10px;" />

#### Collaboration & communication

<img src="../images/app_photo_service_problem_troubleshooting_collaboration.png"
     alt="app_photo_service_problem_troubleshooting_collaboration.png"
     style="float: left; margin-right: 10px;" />

#### Break down business logic on the photo service

<img src="../images/app_photo_service_slow_breakdown.png"
     alt="app_photo_service_slow_breakdown.png"
     style="float: left; margin-right: 10px;" />

#### Identify the attributes of the different services?

<img src="../images/app_photo_service_slow_breakdown_identify_attributes_Services.png"
     alt="app_photo_service_slow_breakdown_identify_attributes_Services.png"
     style="float: left; margin-right: 10px;" />

#### Segregate services for better performance and scalability

<img src="../images/app_photo_service_slow_segregates_Services.png"
     alt="app_photo_service_slow_segregates_Services.png"
     style="float: left; margin-right: 10px;" />

#### What about our Service Level Objectives (SLOs) and Indicators (SLIs)

<img src="../images/app_photo_service_slow_new_SLO_SLI.png"
     alt="app_photo_service_slow_new_SLO_SLI.png"
     style="float: left; margin-right: 10px;" />

### Design challenge #1: Log aggregation

This lesson introduces a related independent design problem, the **log files**.

On the original single virtual machine solution, all of the log files were stored on the instance. As the design changes, new complications are introduced into the design of a log system. To meet troubleshooting requirements, the separate logs will need to be aggregated onto a single system. Watch the lesson that describes the problem and then come up with your own solution. When you're ready, continue the lesson to see a sample solution. Remember that the sample solution is not the best possible solution, it's just an example, your design might be better


<img src="../images/challenge_log_files.png"
     alt="challenge_log_files.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/challenge_log_files_segregated.png"
     alt="challenge_log_files_segregated.png"
     style="float: left; margin-right: 10px;" />

What that means is, we have two different log entries now, one for the web and one for the application. They do share a common session ID fields so we need to have a process that will join those together for troubleshooting.


 we have logs on two servers, we're going to aggregate them into a single log. So, the solution here is to design a logging server. This server will accept logs, perhaps we're just using sys log fluid d or something else like that, maybe even Kafka. So, in this case we're going to create, let's call this a Python script. We're just going to whip something together, we're going to have a daily cron job that's going to take all these log files and it's going to aggregate them. So, it's purpose is to ingest that data to open the log files together, so it pushes them together. Then we need to transform them. So, even though they're all in one file, we're going to transform them and join them on that session ID. Then we're going to output that data and now we have aggregate log files. Then the daily cron job will go ahead and repeat itself. So, every 24 hours, we will have combined logs. 

<img src="../images/challenge_log_files_segregated_implement_logging_server.png"
     alt="challenge_log_files_segregated_implement_logging_server.png"
     style="float: left; margin-right: 10px;" />

**New business logic:**

<img src="../images/challenge_log_files_segregated_implement_logging_server_new_business_logic.png"
     alt="challenge_log_files_segregated_implement_logging_server_new_business_logic.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/challenge_log_files_slow_new_business_logic_output_numbers_for design.png"
     alt="challenge_log_files_slow_new_business_logic_output_numbers_for design.png"
     style="float: left; margin-right: 10px;" />


### lab: useDeployment Manager: Package and Deploy

In this lab, you'll learn:

- how to customize an instance using the deployment manager template. 
- how to install library packages and software required of an application.
- how to package and install a Python application, the Echo application, that will be installed at boot time and will run when the instance starts up.

The application development team is supposed to provide an early version of the photo application for you to start building the infrastructure, but they're late. Instead, they provide a similar Python application, called Echo for you to use until the real app is ready. Note that you'll not need to do any programming for this lab. The application is already written. You'll just be creating and configuring the templates. Your challenge in this lab is to use deployment manager templates to create the app server. You'll need to package and install the pre-written Python application. You'll need to install the required application frameworks that the application depends on. And you'll need to handle environment metadata to customize and initialize the server during the boot process.


**Qwiklabs – Deployment Manager Package and Deploy**

In this lab you will...

* Develop a service using a pre-written Python application called "Echo" and example Deployment Manager templates written in YAML and JINJA2.
* Create a deployment package suitable for Deployment Manager using the python package manager, pip.
* Stage your package in a Cloud Storage bucket.
* Manually test the application to ensure that it is working properly.
* Use Deployment Manager to deploy the Echo service.
* Test the new service.

- [video lab overview](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/V7NHs/deployment-manager-package-and-deploy)
- [lab notes](../labs/lab_design_and_process_develop_and_deploy_a_service_with_deployment_manager.md)





## Data Layer Design

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/Sw0BJ/data-layer-design-overview)

The data layer covers the storage and retrieval of data, including the mechanisms of storage and retrieval, such as databases and file systems, and including the access methods that use the services, such as SQL and API's. However, what's not covered in this module is the transport of data into, around, and out of the system. The networking transport of data is covered in the presentation layer module.

The data layer includes; the data persistent mechanisms, such as the database services and storage services, and the data access layer, which encapsulates the persistent mechanisms and exposes the data.

<img src="../images/Data_layer_design_data_layer.png"
     alt="Data_layer_design_data_layer.png"
     style="float: left; margin-right: 10px;" />

### Classifying and Characterizing Data

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/2FsRQ/data-layer-design-classifying-and-characterizing-data)

There are many ways to characterize data such as structured or unstructured, persistent or ephemeral. This lesson focuses on characterizing data based on what the user cares about. Most often, the user doesn't care about the underlying technology, but about whether the data is accessible when they need it. And whether the data they retrieve is the same data they stored and not modified or altered.


<img src="../images/dummyData_layer_design_data_integrity.png"
     alt="dummyData_layer_design_data_integrity.png"
     style="float: left; margin-right: 10px;" />

What users really care about is **data integrity**.

They can't really distinguish the difference between:

- data loss,
- data corruption,
- extended unavailability.

If their data's not there, it might as well be gone.

However, as an engineer, persistence and access are very separate. Access, basically, is a loss of data access, is very important to users, but that doesn't mean that our data is gone. Persistence and proactive detection and rapid recovery is really what our goal is. If there is data that is somehow lost we want to be able to get it back, **recover it maybe using version controls or backups**. **Or some kind of failover mechanism**.

<img src="../images/Data_layer_design_data_transaction_property.png"
     alt="Data_layer_design_data_transaction_property.png"
     style="float: left; margin-right: 10px;" />

So when you're thinking about your data, you need to think about what data transaction properties are going to be required. And, of course, you have your menu, and **you can only really pick two**, and this is the **CAP Theorem**. So here you have to choose between:
- **consistency**,
- **availability**, 
- and **partition tolerance**.


#### BASE

If you want availability and partition tolerance, you can go over to BASE, which is **Basically Available Storage**. It's soft state and it's going to be eventual consistency. Now, what that means is, you may make an update, it may not be available there immediately. Or specific changes may not necessarily be available. But with that type of ability, it allows you to write data, it allows you to expand your data very, very quickly. And eventually everything will all be consistent.

#### ACID

Now if you want pure consistency, then we get into what we call ACID transactions. Which stands for **Atomicity, Consistency, Isolation,** and **Durability**. That means if you write some data to your data storage system, it is guaranteed to be there. You will not get an acknowledgement until it has been written and it is completely fault-tolerant, replicated, et cetera. So it will ensure any type of failover capabilities.

#### What are the data consistency requirements?

<img src="../images/Data_layer_design_data_consistency_requirements.png"
     alt="Data_layer_design_data_consistency_requirements.png"
     style="float: left; margin-right: 10px;" />

#### What are you truing to optimize? Domain/App specific

- uptime
- latency
- scale
- velocity
- privacy

<img src="../images/Data_layer_design_data_consistency_requirements_what_to_optimize.png"
     alt="Data_layer_design_data_consistency_requirements_what_to_optimize.png"
     style="float: left; margin-right: 10px;" />

### Data Ingest and Data Migration

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/yWyty/data-layer-design-data-ingest-and-data-migration)

**Data migration** is the idea that data already exists somewhere and that it will be transported into the cloud. Once the base of existing data has been migrated, updates and new data will be added to the cloud version and the original is no longer needed.

**Data ingestion** is the idea that data will continue to originate outside of the cloud and will be periodically loaded into the cloud.

This lesson covers the most **common methods for getting data into the cloud**.

#### GCS migration tools: console, gsutil, JSON API

<img src="../images/Data_layer_design_Data_migration_tools_on_GCP.png"
     alt="Data_layer_design_Data_migration_tools_on_GCP.png"
     style="float: left; margin-right: 10px;" />

About data migration. We need to bring data into our system and we potentially need to migrate it from different locations.

So there's a few ways that we do this:

* One is directly from the **console for GCS**, you can just drag and drop files.
* There's the **`gsutil` for the Google storage utility command**. This also has the built in Amazon S3 SDK so it allows us to transfer data from Amazon buckets on ourselves. But it also gives us capability to do identity access management, sign URLs, access control lists. There's a whole bunch of capabilities just from this command line.
* And then of course, our **JSON API**. So here you can make the API calls yourself, you can compress this data, and you can also do partial uploads which is really good especially because most uploads to GCS buckets are going to be entire updates. And so in this case here, if you control the API, you might be able to have a little bit more efficiency built in.


#### GCS migration tools for large transfers: Cloud Storage Transfer Service

<img src="../images/Data_layer_design_Data_migration_tools_on_GCP_large_trasnfers.png"
     alt="Data_layer_design_Data_migration_tools_on_GCP_large_trasnfers.png"
     style="float: left; margin-right: 10px;" />

Now we also have a commercial service, well not a commercial, but it's a service that is designed for very large transfers, and it's called the **Cloud transfer service**. It's basically a web based interface that's using a lot of the APIs in the back end to transfer data between say, Amazon and us, and it does so very efficiently. Now it usually recommends typically over a terabyte worth of data because it can do a lot of management like deleting the source data, making sure one is synchronized, overriding any changes, but optimizes the number of streams as well. So it looks at that source material says, how many of them are there? I will create an optimized number of streams to ensure we can get this moved over as fast as possible.

#### GCS migration tools for large transfers without network: Google Transfer Appliance

<img src="../images/Data_layer_design_Data_migration_tools_on_GCP_trasnfers_appliance.png"
     alt="Data_layer_design_Data_migration_tools_on_GCP_trasnfers_appliance.png"
     style="float: left; margin-right: 10px;" />

Now of course, the size always does matter and if you need to be transferring hundreds of terabytes of data, perhaps, you don't want to do that over the network. Even though ingress is free, it may not be time efficient. So we now have the transfer appliance very similar to Amazon's Snowball capability. It's an appliance that ships on site, you can either rock it or do it as a off-the-shelf appliance up to a petabyte worth of storage. And this way, you can copy all the data on your local network and then ship it to Google for data ingest.
 
#### GCS migration tools scal-up table

<img src="../images/Data_layer_design_Data_migration_tools_summary_table_scaleup.png"
alt="Data_layer_design_Data_migration_tools_summary_table_scaleup.png"
style="float: left; margin-right: 10px;" />


Here's a fun little table to kind of give you an idea. When you really start to scale up and the amount of data you need to move over to us, you also have to scale up in the amount of bandwidth that you might have capable. Now, even at 10 gigs fully saturated, 30 hours is pretty considerable but, I wouldn't say considerable. The fact that you probably cannot utilize that full amount of bandwidth yourself and this is where you'll start to see some serious delays in a larger data transfer. So just kind of use this and we do recommend using the Google transfer appliance probably between 10 and 100 terabytes just to make your life a little easier.

#### Data ingestion tools

<img src="../images/Data_layer_design_Data_ingestion_tools.png"
     alt="Data_layer_design_Data_ingestion_tools.png"
     style="float: left; margin-right: 10px;" />

  
So other ways that we ingest data into your service.

* Now first, obviously, it can be done **through the network** which is going to be, its globally available, it's highly available, there's a bandwidth of a 100 gigs and many of our peering locations in low latency.
* You can post directly **to cloud storage using HTTP, RESTful APIs**.
* You can put front end application **through App Engine**. So this way, we can build an authentication, integrate that way, even cloud endpoints.

So we can expose just a simple API that can ingest data into your application even through cloud functions, or set up a computer engine instance and store it on local persistent disk. There's a number of different ways to bring data in, some of them have various pros and cons which we can cover.


### Identification of Storage Needs and Mapping to Storage Systems

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/dQlqJ/data-layer-design-identification-of-storage-needs-and-mapping-to-storage-systems)

Google Cloud Platform offers a wide variety of storage and database services.

This lesson provides a general **method to narrow down the list of candidates storage services**. The diagrams and charts in this lesson can help you ask meaningful questions about the data that will help you match the data to storage services.

#### Choose a storage solution between: DISK, MOBILE or CLOUD solutions

<img src="../images/Data_layer_design_GCP_solution_Disk-or-Mobile-or-Cloud.png"
     alt="Data_layer_design_GCP_solution_Disk-or-Mobile-or-Cloud.png"
     style="float: left; margin-right: 10px;" />

#### Choose a storage solution for unstructured data on Cloud Storage: regional, multi-regional, nearline, coldline

<img src="../images/Data_layer_design_Coud_Storage_regional_coldline_nearline.png"
     alt="Data_layer_design_Coud_Storage_regional_coldline_nearline.png"
     style="float: left; margin-right: 10px;" />

#### Choose a storage solution for analytics: BigQuery

<img src="../images/Data_layer_design_Why_choose_BigQuery.png"
     alt="Data_layer_design_Why_choose_BigQuery.png"
     style="float: left; margin-right: 10px;" />

#### Choose a storage solution for SQL (scalable or not): Clud SQL or Spanner

<img src="../images/Data_layer_design_Why_choose_if_SQL.png"
     alt="Data_layer_design_Why_choose_if_SQL.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Data_layer_design_Why_choose_if_SQL_scalable.png"
     alt="Data_layer_design_Why_choose_if_SQL_scalable.png"
     style="float: left; margin-right: 10px;" />

#### Choose a storage solution for NoSQL: Cloud Datastore

<img src="../images/Data_layer_design_Why_choose_if_NoSQL.png"
     alt="Data_layer_design_Why_choose_if_NoSQL.png"
     style="float: left; margin-right: 10px;" />

#### Choose a storage solution: decision tree & summary table

<img src="../images/Data_layer_design_GCP_solution_decision_tree.png"
     alt="Data_layer_design_GCP_solution_decision_tree.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Data_layer_design_GCP_solution_summary_table.png"
     alt="Data_layer_design_GCP_solution_summary_table.png"
     style="float: left; margin-right: 10px;" />


### Application: The photo service experiences Intermittent Outages

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/1NbrK/intermittent-outages)

There's something wrong with the photo application.

Occasionally, the service simply fails to produce the smaller preview image. This used to suddenly occur, but in recent weeks the frequency appears to be increasing and it is becoming a problem recognize by users. The issue appears to be **random**. 

- What's happening?
- and how can you change the design to fix this problem? 

#### Business problem

<img src="../images/app_photo_service_intermittent_outages.png"
     alt="app_photo_service_intermittent_outages.png"
     style="float: left; margin-right: 10px;" />



#### Systematic logical troubleshooting

<img src="../images/app_photo_service_intermittent_outages_analysis.png"
     alt="app_photo_service_intermittent_outages_analysis.png"
     style="float: left; margin-right: 10px;" />

- systematic & logical troubleshooting
- and answering the ["five why's"](https://en.wikipedia.org/wiki/Five_Whys)


The team has determined that the root problem, is the persistent disk on the application server cannot keep up with the scale of demands being placed on it. All right. So, that's the thing. You can scale up CPU, but sometimes your underlying disk IO performance cannot keep up. As well as something that most people don't think about, is disk IO also does need some CPU? So, that could be a problem. But in this case, we're focusing strictly on that. There's not enough virtual machine disc IO power to handle this kind of scale that we're looking at.

#### Break down business logic on the photo service

<img src="../images/app_photo_service_refreshed_business_logic.png"
     alt="app_photo_service_refreshed_business_logic.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/app_photo_service_business_logic_with_bottleneck.png"
     alt="app_photo_service_business_logic_with_bottleneck.png"
     style="float: left; margin-right: 10px;" />

with 1 millions pictures per day, we need to move from our local file system to Cloud Storage for scalability.

#### New Service Level Objectives (SLOs) and Indicators (SLIs)

we're going to introduce some **new service level objectives**.

In this case here, we want to **reduce the error rate**. So, we want to keep the failures to produce a thumbnail down below, less than one 10th of one percent. So, that's **about 100 errors per million images**.

Now, how are we going to measure this? While our service level indicators are going to look at the logs and we're going to identify if there's any logs that failed to, if they indicate any type of errors. So, this means that **our error budget is going to be 3,000 errors per month**. 

Now, one of the things that our IOs do, is they are allocated an error budget. As long as they stay within that budget, then they can work on future things. But if they're unable to remain within their error budget during the month, then they will have to focus on automation and tools, and whatever it takes, to ensure that they can now meet that error budget month after month before they can work on new things, or just simply take a break, right? Because that's really the goal, you don't want your SRE is working full time. They should only be working about half the time and if they are, it should be either responding to requests or developing for future uses. Take the job of a firefighter, they're always on-call, always on edge, but they're not physically working all the time. If you did that, then they wouldn't be able to offer that same kind of response.

<img src="../images/app_photo_service_outages_new_service_levels.png"
     alt="app_photo_service_outages_new_service_levels.png"
     style="float: left; margin-right: 10px;" />

### Design challenge #2: Complication

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/XVrs7/design-challenge-2-complication)

In the application lesson, the random intermittent failure turned out to be a **capacity issue**. The services simply couldn't keep up with the demand and you're able to redesign a solution to add a storage service component in addition to the web server component and the thumbnail processing app server component. 

This leads to **another problem in the log aggregation system**: The log aggregator needs to account for another source of log entries and **the log aggregation servers running out of disk space**. Take a closer look at this problem. 

Your challenge is to **modify the log aggregation design to avoid or overcome this issue**. Watch the lesson that describes the problem, then come up with your own solution. When you're ready, continue the lesson to see a sample solution. Remember that the sample solution is not the best possible solution. it's just an example and your design might 


<img src="../images/app_photo_service_capacity_problem_for_log_aggregation.png"
     alt="app_photo_service_capacity_problem_for_log_aggregation.png"
     style="float: left; margin-right: 10px;" />

**Business logic**

<img src="../images/app_photo_service_capacity_problem_for_log_aggregation_new_business_logic.png"
     alt="app_photo_service_capacity_problem_for_log_aggregation_new_business_logic.png"
     style="float: left; margin-right: 10px;" />

- Why not **GCS** for aggregating this log files?

<img src="../images/app_photo_service_capacity_problem_for_log_aggregation_properties.png"
     alt="app_photo_service_capacity_problem_for_log_aggregation_properties.png"
     style="float: left; margin-right: 10px;" />

- Why not **Bigtable** for aggregating this log files?

<img src="../images/app_photo_service_capacity_problem_for_log_aggregation_Bigtable.png"
     alt="app_photo_service_capacity_problem_for_log_aggregation_Bigtable.png"
     style="float: left; margin-right: 10px;" />

## Presentation Layer Design

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/hpapG/presentation-layer-design-overview)

### Overview

The **presentation layer** has to do with the **flow of data through the system** between the user, business logic, and the stored service, aka **this is the network**:

- the **network edge configuration**,
- the **network configuration for data transfer** within the service,
- and **network integration** with other environments. 

#### Network Configuration

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/LOWWt/presentation-layer-network-configuration)

One key point of this lesson is a **location within the cloud network makes a difference in latency**.

In general, there's a direct tradeoff: the more distributed elements are in your design, the more tolerant the system will be of outages. However, there are real performance limitations because the round trip time is much slower between distant elements. And there are expense considerations for egress traffic. The critical technology to implementing Intelligent Traffic Management in the design is **load balancing**. Fortunately, the platform offers a very robust set of load balancing services that are optimized for different circumstances

So, network configuration for data transfer within the service, all is going to focus on:

- **location**,
- **load balancing**, 
- and **caching**.

##### Impact of Location

<img src="../images/Presentation_layer_Network_location.png"
     alt="Presentation_layer_Network_location.png"
     style="float: left; margin-right: 10px;" />

So the location of resources within the cloud is, within the cloud network, I should say, is very significant. So, when you take a look here at you know a million nanoseconds is one millisecond, depending on what network you choose, if you're going to choose say a two kilobyte packet over one gig network, you can do this in 2000 of a second. Now, what about a roundtrip within the same data center? Google's data centers are pretty fast, you can get away with half a millisecond, sometimes even faster, depending on the design. Now,what if you wanted to send something across the world, from say California to the Netherlands and back. Well, that could be upwards of 150 milliseconds. Yes, even that is considerably fast due to Google's global fiber network. However, these are design considerations you need to take place. Especially, if you're looking at the perspective of the user or your specific application. So remember, no more than six to seven round trips between Europe and US per second are possible but approximately 2000 per second can be achieved within a data center. And these are important generalizations, understand whether it's time to push data closer to the user or actually locate your application in multiple different data centers themselves. So the technology that allows you to control the network location of resources used by your service is going to be called Load balancing.

##### Impact of Load Balancing

So the technology that allows you to control the network location of resources used by your service is going to be called Load balancing. Now load balancing in our world is a little bit different. So, basically what it does, it's getting user traffic to the application servers with capacity in the closest region to that customer. Unless you know if you have no load balancing sometimes it's going to be internal distribution of traffic across a multiple servers inside of your application infrastructure. It can also trigger auto scaling, but we also provide global load balancers. And that gives you a single external IP address that can locate, or I should say, that can send traffic to any geographical location that's closest to your individual user. We offer many different kinds of load balancing services and they're each optimized for each different use case

<img src="../images/Presentation_layer_Network_load_balancing.png"
     alt="Presentation_layer_Network_load_balancing.png"
     style="float: left; margin-right: 10px;" />

**Global Load Balancers**

<img src="../images/Presentation_layer_Network_global_load_balancers.png"
     alt="Presentation_layer_Network_global_load_balancers.png"
     style="float: left; margin-right: 10px;" />

##### Choosing your type of load balancer

<img src="../images/Presentation_layer_Network_choosing_your_load_balancers.png"
     alt="Presentation_layer_Network_choosing_your_load_balancers.png"
     style="float: left; margin-right: 10px;" />


#### Integration with other Environments

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/oiQOu/presentation-layer-integration-with-other-environments)



##### Network edge configuration for users and clients

<img src="../images/Presentation_layer_Network_global_IP_adresses.png"
     alt="Presentation_layer_Network_global_IP_adresses.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Presentation_layer_Network_Cloud_CDN.png"
     alt="Presentation_layer_Network_Cloud_CDN.png"
     style="float: left; margin-right: 10px;" />

https://peering.google.com/#/infrastructure

<img src="../images/Presentation_layer_Network_Edge_infrastructure.png"
     alt="Presentation_layer_Network_Edge_infrastructure.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Presentation_layer_Network_Edge_infrastructure_datacenters.png"
     alt="Presentation_layer_Network_Edge_infrastructure_datacenters.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Presentation_layer_Network_Edge_infrastructure_PoPs.png"
     alt="Presentation_layer_Network_Edge_infrastructure_PoPs.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/Presentation_layer_Network_Edge_infrastructure_edge_nodes.png"
     alt="Presentation_layer_Network_Edge_infrastructure_edge_nodes.png"
     style="float: left; margin-right: 10px;" />

In order to use the CDN, you have to turn on HTTP(S) load balancing or other network load balancing. But in this case here, you can actually push and publish content directly from Google Cloud stores to the CDN. But if you want to use it from the network layer, we can automatically start to cache any data that goes through our HTTP(S) load balancer. So that's a kind of a huge benefit


##### Network connections to other networks (e.g. data center, another cloud)

###### Dedicated interconnects

<img src="../images/Presentation_layer_Network_interaction_with_other_cloud_providers.png"
     alt="Presentation_layer_Network_interaction_with_other_cloud_providers.png"
     style="float: left; margin-right: 10px;" />

The big thing in the middle is you need to have some kind of dedicated interconnect. So, we have what's called a cloud partner interconnect or even dedicated connections which can connect us to other providers. So in this case here, we can actually have private bandwidth between both cloud providers. And of course, if you have the proper routing between the two, we can route those networks equally between the two different locations. 

###### VPN configurations

<img src="../images/Presentation_layer_Network_interaction_with_other_cloud_providers_VPNs.png"
     alt="Presentation_layer_Network_interaction_with_other_cloud_providers_VPNs.png"
     style="float: left; margin-right: 10px;" />

 There's a couple of ways to do that by **taking advantage of VPNs**:
 
 - you can **aggregate multiple VPN gateways** to try to aggregate the bandwidth to the other provider.
 - you can also **do this in reverse**. And in this case, we usually allow about 1.5Gb per VPN tunnel. So this way you can aggregate these together or create a fully mesh network. So this way, you have fell over in case the remote VPN gateway fails, you have backup links et cetera, just standard networking redundancy built in.
 
 And so, all of this is really available through **Cloud Router**. Again either setting static routes or dynamic routes. So if you're making network changes at the cloud provider and spinning up new subnets that might be custom, you want to make sure that the Google Cloud platform also knows about that, and you take advantage of our cloud routing service to make sure that notifications are possible. 

**VPN Performances**

<img src="../images/Presentation_layer_Network_interaction_with_other_cloud_providers_VPNs_performances.png"
     alt="Presentation_layer_Network_interaction_with_other_cloud_providers_VPNs_performances.png"
     style="float: left; margin-right: 10px;" />

### Application: Photo service... Periodic Slowdowns

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/YMh4S/period-slowness-in-application)

#### Business problem

The photo services working fine, however, recently there have been periodic slowdowns, users are experiencing delays, it's taking an increasingly long time for the system to respond with a thumbnail image. Then, after some time, it appears to speed up again.

<img src="../images/app_photo_service_periodic_slowdown.png"
     alt="app_photo_service_periodic_slowdown.png"
     style="float: left; margin-right: 10px;" />

What could possibly be the cause of the slowdown?

what can you do to change the design to overcome this problem?

#### Systematic logical troubleshooting


<img src="../images/app_photo_service_periodic_slowdown_troubleshooting_miscommunication.png"
     alt="app_photo_service_periodic_slowdown_troubleshooting_miscommunication.png"
     style="float: left; margin-right: 10px;" />

#### Collaboration & communication: Report, Document, build policy

<img src="../images/app_photo_service_periodic_slowdown_build_process_to_learn_from_mistakes.png"
     alt="app_photo_service_periodic_slowdown_build_process_to_learn_from_mistakes.png"
     style="float: left; margin-right: 10px;" />

you have to document it, while it might be viewed as a really boring process and most people complain about having to do it you always want to create reports, but under what conditions. Well, for starters, anytime an SLO is breached, any incident that requires emergency on-call, also if there's a need for follow-up communications for example, if legal need to explain an outage without revealing the impact or something competitive. There needs to be a clear policy that defines the writing of these reports. Timelines must be specified in terms of how soon after an incident a draft is going to be published, as well as a timeline for completing the report. So, writing these reports creates a record of what happened and what was done to fix it. This will be a helpful source of reference in the future if a similar event happens again, so **doing these postmortems should be a mandatory part of your recovery processes**.

<img src="../images/app_photo_service_periodic_slowdown_report_document_write_policy.png"
     alt="app_photo_service_periodic_slowdown_report_document_write_policy.png"
     style="float: left; margin-right: 10px;" />


#### Break down business logic on the photo service

<img src="../images/app_photo_service_periodic_slowdown_business_logic_refresher.png"
     alt="app_photo_service_periodic_slowdown_business_logic_refresher.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/app_photo_service_periodic_slowdown_business_logic_refresher_issue.png"
     alt="app_photo_service_periodic_slowdown_business_logic_refresher_issue.png"
     style="float: left; margin-right: 10px;" />

 It's taking minutes to generate thumbnails. So, the system is definitely slow. A systematic and logical troubleshooting process has been followed in the "five why's" have been asked and answered. The conclusion is that the issue is definitely tied to the capacity of the system to generate thumbnails. It's also been established that it isn't the front-end web server is causing the delays, but the back-end thumbnail generating service, which is failing to keep up with demand. When we say capacity, it's the capacity to actually perform the service in a timely manner. So, what happens, **the thumbnail is running out of CPU**. We could watch CPU utilization, but CPU utilization isn't linear and during busy utilization times, it can go to 100%. This is sure to impact the end-to-end response time for the user.
 
 - How do you monitor it?
 - How do you alert on this? You need to be able to look at specific windows.
 - Depending on how long it should be for the average thumbnail to respond instead of looking over five minutes, maybe need to look over a minute.
 - But keep in mind, CPU utilization is not actually to be used as a service level indicator.

**Solution**: Scale out the backend processing of thumbnails.

<img src="../images/app_photo_service_periodic_slowdown_business_logic_solution.png"
     alt="app_photo_service_periodic_slowdown_business_logic_solution.png"
     style="float: left; margin-right: 10px;" />

Here's our decision, we decided that if we need to handle more thumbnail processing, it's got to become more scalable. However, we didn't choose to simply throw more CPU and network at it because it was more of a single point of failure. Instead we decided to add a load balancer and scale out the number of thumbnail servers. The great thing is that it's like micro servers in itself now, because storage has been isolated to Google Cloud Storage, the same code can be distributed and it doesn't keep track of a queue or anything else. The Upload Server basically pulls whatever is on the Data Storage Server and it load balances it as they come in. Technically, this is probably an internal load balancer, but we'll get into that a little bit later.

In this case, to help us with our greater than 80 percent CPU utilization, **we want to distribute traffic request from our business logic to the Application Servers in a cluster**.


#### What about our Service Level Objectives (SLOs) and Indicators (SLIs)

Even though we've added a cluster of servers, we haven't changed anything that our users can measure. The performance is still a measure of the end-to-end latency and the accuracy of the service is still based on the error logs.

<img src="../images/app_photo_service_periodic_slowdown_business_logic_SLIs_SLOs_unchanged.png"
     alt="app_photo_service_periodic_slowdown_business_logic_SLIs_SLOs_unchanged.png"
     style="float: left; margin-right: 10px;" />

### Design challenge #3: Growth

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/k6rt9/design-challenge-3-growth)

In the application lesson, you overcame the periodic slow downs by increasing capacity of the thumbnail application component, replacing the single server with a group of load balanced auto scaling servers.

That means instead of a single app server log, you now have logs coming from each server in the pool. **How can you evolve the design of the log aggregation system to accommodate the new scalable service?** Watch the lesson that describes the problem, then come up with your own solution. When you're ready, continue the lesson to see a sample solution. Remember that the sample solution is not the best possible solution, it's just an example and your design might be better.

<img src="../images/app_photo_service_periodic_slowdown_design_challenge_logs_of_a cluster.png"
     alt="app_photo_service_periodic_slowdown_design_challenge_logs_of_a cluster.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/app_photo_service_periodic_slowdown_design_challenge_logs_of_a cluster_problem.png"
     alt="app_photo_service_periodic_slowdown_design_challenge_logs_of_a cluster_problem.png"
     style="float: left; margin-right: 10px;" />

Let's define the problem. So in our case autoscaling of the application servers has produced logs that are outgrowing the processing capacity of the aggregation logging server. So in this case we want to design a solution. Now always remember, there are multiple designs that you can take, right? Your solution may be better, and that's okay. But let's at least work through the different solutions, decide what we want to take advantage of next. And what we hear too, hey, now do we move to data flow? Well, maybe. But let's think about what that might do, and these are dialogues I've had with students in class. This is a Python script, and well, data flow does support Python. So that didn't work because, but maybe to do what we want to do, it requires the Java version of the SDK. And that would mean that our programmer who designed this and just threw this together, is going to have to learn a new language. Now you could say, hey that's expected, but these are potential limitations. So if you look at a new service, what are the requirements of that new service to make it happen? Even though on paper it may sound good, you can just swap it out. But in order to rewrite the code and there might be a learning curve, etc. So in this case, our guy is, you know, this would be a lot easier if all we did was design this so it could scale. So one simple solution, and iteratively was let's go ahead and **put an internal load balancer here, so this way, our logging server can run on multiple instances**. So here we have an auto scaling instance group. It can take logs as they're ingested and it can put them directly inside of Big Table. All right, so now we can run our queries, get our session IDs, and we don't have to really worry about this failing. So really, this scales rather nicely, because we will have a daily cron job that will take all the local data storage and process that in.

<img src="../images/app_photo_service_periodic_slowdown_design_challenge_logs_of_a cluster_solution_load_balancer_on_logs_servers.png"
     alt="app_photo_service_periodic_slowdown_design_challenge_logs_of_a cluster_solution_load_balancer_on_logs_servers.png"
     style="float: left; margin-right: 10px;" />

### lab: Autoscaling

- [video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/55yny/lab-intro-autoscaling)
- [lab notes](../labs/lab_deployment_manager_Adding_load_balancing_for_autoscaling.md)


The photo application that was promised by the development team is late. You decide that you don't want to wait any longer to develop the infrastructure. When the photo app does become available, you don't want to add to the schedule delay, so you decide to make the infrastructure auto-scaling and reliable by building on a previous deployment. This way, when the photo app is available you can just drop it in to the deployment framework that you've built. The deployment manager templates from the previous lab will be provided to you in a TAR file, so you'll just be creating the additional files.

<img src="../images/lab_deployment_autoscaling_app.png"
     alt="lab_deployment_autoscaling_app.png"
     style="float: left; margin-right: 10px;" />




## Resources/Articles

- https://cloud.google.com/compute/docs/reference/rest/v1/instances
- Common design patterns: https://cloud.google.com/apis/design/design_patterns

# Design for Resiliency, Scalability, Disaster Recovery & Security

- **Resiliency, Scalability, Disaster Recovery**: Implement technologies and processes that assure business continuity in the event of a disaster.
- **Security**: Implement policies that minimize security risks, such as auditing, separation of duties and least privilege.
- **Capacity Planning & Cost Optimization**: Identify ways to optimize resources and minimize cost.
- **Deployment, Monitoring and Alerting, and Incident Response**

## Content

* [Detailled Content](#detailled-content)
* [Design for Resiliency, Scalability, and Disaster Recovery](#design-for-resiliency-scalability-and-disaster-recovery)
   * [Overview](#overview)
   * [Failure Due to Loss](#failure-due-to-loss)
   * [Failure Due to Overload](#failure-due-to-overload)
   * [Coping with Failure](#coping-with-failure)
   * [Business Continuity &amp; Disaster Recovery](#business-continuity--disaster-recovery)
   * [Scalable &amp; Resilient Design](#scalable--resilient-design)
   * [Application: Out of Service!](#application-out-of-service)
   * [Design Challenge #4: Redesign for Time](#design-challenge-4-redesign-for-time)
* [Design for Security](#design-for-security)
   * [Overview](#overview-1)
   * [Cloud Security](#cloud-security)
   * [Network Access Control &amp; Firewalls](#network-access-control--firewalls)
   * [Protections Against Denial of Service](#protections-against-denial-of-service)
   * [Resource Sharing &amp; Isolation](#resource-sharing--isolation)
   * [Data Encryption &amp; Key Management](#data-encryption--key-management)
   * [Design for Security: Identity Access &amp; Auditing](#design-for-security-identity-access--auditing)
   * [Application: Photo Service - Intentional Attack](#application-photo-service---intentional-attack)
   * [Design Challenge #5: Defense in Depth](#design-challenge-5-defense-in-depth)
* [Capacity Planning &amp; Cost Optimization](#capacity-planning--cost-optimization)
   * [Overview](#overview-2)
   * [Capacity Planning](#capacity-planning)
   * [Pricing](#pricing)
   * [Application: Photo Service - Cost &amp; Capacity](#application-photo-service---cost--capacity)
   * [Design Challenge #6: Dimensioning](#design-challenge-6-dimensioning)
* [Deployment, Monitoring and Alerting, and Incident Response](#deployment-monitoring-and-alerting-and-incident-response)
   * [Learning Objectives](#learning-objectives)
   * [Overview](#overview-3)
   * [Deployment](#deployment)
   * [Monitoring &amp; Alerting](#monitoring--alerting)
   * [Incident Response](#incident-response)
   * [Application: Stabilization &amp; Operation](#application-stabilization--operation)
   * [Design Challenge #7: Monitoring &amp; Alerting](#design-challenge-7-monitoring--alerting)
   * [Lab: Deployment Manager - Full Production](#lab-deployment-manager---full-production)
* [Resources/Articles](#resourcesarticles)

## Detailled Content

* [Content](#content)
* [Detailled Content](#detailled-content)
* [Design for Resiliency, Scalability, and Disaster Recovery](#design-for-resiliency-scalability-and-disaster-recovery)
   * [Overview](#overview)
   * [Failure Due to Loss](#failure-due-to-loss)
      * [Failure is mandatory](#failure-is-mandatory)
      * [Single Point of failure](#single-point-of-failure)
      * [Design to avoid Single Point of failure: N 2 (a spare spare)](#design-to-avoid-single-point-of-failure-n2-a-spare-spare)
      * [Correlated failures](#correlated-failures)
      * [Design to avoid correlated failures](#design-to-avoid-correlated-failures)
   * [Failure Due to Overload](#failure-due-to-overload)
      * [Failover design for reliability](#failover-design-for-reliability)
      * [Cascading failures](#cascading-failures)
      * [Design to avoid Cascading failures](#design-to-avoid-cascading-failures)
      * [Queries-of-Death overload failure](#queries-of-death-overload-failure)
      * [Positive feedback cycle overload failure](#positive-feedback-cycle-overload-failure)
      * [Detect overload early: Early warning systems (<em>canaries</em>)](#detect-overload-early-early-warning-systems-canaries)
   * [Coping with Failure](#coping-with-failure)
      * [Forest fires or Controlled burns](#forest-fires-or-controlled-burns)
      * [Prepare the team](#prepare-the-team)
      * [Incorporate failure into SLOs](#incorporate-failure-into-slos)
      * [Monthly meetings to build processes](#monthly-meetings-to-build-processes)
      * [Strategies for dealing with failure](#strategies-for-dealing-with-failure)
   * [Business Continuity &amp; Disaster Recovery](#business-continuity--disaster-recovery)
      * [Cloud DNS: 100\x availability](#cloud-dns-100-availability)
      * [Data Integrity](#data-integrity)
      * [Reliable recovery with Lazy Deletion](#reliable-recovery-with-lazy-deletion)
      * [backup, archive, RESTORE!](#backup-archive-restore)
      * [Tiered backup for resiliency](#tiered-backup-for-resiliency)
         * [Cloud Storage features for backup and DR](#cloud-storage-features-for-backup-and-dr)
      * [Prepare the team for disasters](#prepare-the-team-for-disasters)
   * [Scalable &amp; Resilient Design](#scalable--resilient-design)
      * [Design pattern: General design for scalable &amp; resilient apps](#design-pattern-general-design-for-scalable--resilient-apps)
      * [Microservices design for scalable &amp; resilient streaming](#microservices-design-for-scalable--resilient-streaming)
      * [12-factor system &amp; application design in GCP](#12-factor-system--application-design-in-gcp)
      * [Processes for simple, iterative, aligned development](#processes-for-simple-iterative-aligned-development)
   * [Application: Out of Service!](#application-out-of-service)
      * [Business problem](#business-problem)
      * [Systematic logical troubleshooting](#systematic-logical-troubleshooting)
      * [Collaboration &amp; communication: Report, Document, build policy](#collaboration--communication-report-document-build-policy)
      * [Break down business logic on the photo service](#break-down-business-logic-on-the-photo-service)
      * [What about our Service Level Objectives (SLOs) and Indicators (SLIs)](#what-about-our-service-level-objectives-slos-and-indicators-slis)
   * [Design Challenge #4: Redesign for Time](#design-challenge-4-redesign-for-time)
      * [Design Challenge: Log aggregation delayed troubleshooting](#design-challenge-log-aggregation-delayed-troubleshooting)
      * [Troubleshooting &amp; solution](#troubleshooting--solution)
* [Design for Security](#design-for-security)
   * [Overview](#overview-1)
   * [Cloud Security](#cloud-security)
      * [Google's strategy for cloud security: "Pervasive efense in depth"](#googles-strategy-for-cloud-security-pervasive-efense-in-depth)
      * [Cloud Networking Security: Defense in Depth](#cloud-networking-security-defense-in-depth)
   * [Network Access Control &amp; Firewalls](#network-access-control--firewalls)
      * [Firewall configuration: 1st line of defense for access](#firewall-configuration-1st-line-of-defense-for-access)
      * [Design for securely accessing VMs](#design-for-securely-accessing-vms)
      * [API access control with Cloud Endpoints](#api-access-control-with-cloud-endpoints)
   * [Protections Against Denial of Service](#protections-against-denial-of-service)
      * [Edge protections agaisnt DDoS](#edge-protections-agaisnt-ddos)
   * [Resource Sharing &amp; Isolation... a compromise](#resource-sharing--isolation-a-compromise)
      * [VPC isolation through public IPs](#vpc-isolation-through-public-ips)
      * [IP address isolation using VPN tunneling](#ip-address-isolation-using-vpn-tunneling)
      * [Cross-project VPC network peering](#cross-project-vpc-network-peering)
      * [Cross-organization VPC network peering](#cross-organization-vpc-network-peering)
      * [Shared VPC](#shared-vpc)
      * [Isolation through multiple network interface](#isolation-through-multiple-network-interface)
      * [Access GCP services over internal IP](#access-gcp-services-over-internal-ip)
   * [Data Encryption &amp; Key Management](#data-encryption--key-management)
      * [Server-side encryption](#server-side-encryption)
      * [Customer manager encryption keys (CMEK)](#customer-manager-encryption-keys-cmek)
      * [Customer Supplied encryption keys (CSEK)](#customer-supplied-encryption-keys-csek)
      * [Persistent Disk Encrytion with CSEK](#persistent-disk-encrytion-with-csek)
      * [Moore control over encryption](#moore-control-over-encryption)
   * [Design for Security: Identity Access &amp; Auditing](#design-for-security-identity-access--auditing)
      * [Identity Access Management](#identity-access-management)
      * [Service Accounts](#service-accounts)
      * [GCP security auditing with Forseti-security (Open Source)](#gcp-security-auditing-with-forseti-security-open-source)
      * [Cloud Audit Logging](#cloud-audit-logging)
      * [External audits &amp; GCP Standards Compliance](#external-audits--gcp-standards-compliance)
   * [Application: Photo Service - Intentional Attack](#application-photo-service---intentional-attack)
      * [Business problem](#business-problem-1)
      * [Break down business logic on the photo service](#break-down-business-logic-on-the-photo-service-1)
      * [Security checklist](#security-checklist)
   * [Design Challenge #5: Defense in Depth](#design-challenge-5-defense-in-depth)
* [Capacity Planning &amp; Cost Optimization](#capacity-planning--cost-optimization)
   * [Overview](#overview-2)
   * [Capacity Planning](#capacity-planning)
      * [1. Forecast](#1-forecast)
         * [Forecast estimation](#forecast-estimation)
         * [Instance overhead estimation](#instance-overhead-estimation)
         * [Persistent disks estimation](#persistent-disks-estimation)
         * [Network capacity estimation](#network-capacity-estimation)
         * [Workload estimation](#workload-estimation)
      * [Allocate](#allocate)
      * [Approve](#approve)
      * [Deploy](#deploy)
   * [Pricing](#pricing)
      * [Optimize VMs cost](#optimize-vms-cost)
      * [Optimize Disks cost](#optimize-disks-cost)
      * [Optimize Network cost](#optimize-network-cost)
   * [Application: Photo Service - Cost &amp; Capacity](#application-photo-service---cost--capacity)
      * [Business problem](#business-problem-2)
   * [Design Challenge #6: Dimensioning](#design-challenge-6-dimensioning)
      * [Growth status for BigTable](#growth-status-for-bigtable)
* [Deployment, Monitoring and Alerting, and Incident Response](#deployment-monitoring-and-alerting-and-incident-response)
   * [Learning Objectives](#learning-objectives)
   * [Deployment](#deployment)
   * [Monitoring &amp; Alerting](#monitoring--alerting)
      * [SRE pyramid: Monitoring is measuring](#sre-pyramid-monitoring-is-measuring)
      * [Push-based and Pull-based metrics](#push-based-and-pull-based-metrics)
      * [Black box monitoring (affecting user experience)](#black-box-monitoring-affecting-user-experience)
      * [White box monitoring (monitoring services)](#white-box-monitoring-monitoring-services)
      * [Carefully output of monitoring systems: alerts,](#carefully-output-of-monitoring-systems-alerts)
      * [12-factor administration &amp; operation in GCP: Stack driver](#12-factor-administration--operation-in-gcp-stack-driver)
      * [Some features of Stack driver](#some-features-of-stack-driver)
   * [Incident Response](#incident-response)
      * [Structured incident response](#structured-incident-response)
      * [List of SRE processes](#list-of-sre-processes)
      * [12-factor guidelines on administration and management tasks](#12-factor-guidelines-on-administration-and-management-tasks)
      * [Build a playbook based on alerts](#build-a-playbook-based-on-alerts)
         * [Create "easy buttons" for quick fix](#create-easy-buttons-for-quick-fix)
         * [Balance interrupt-driven work and Incident Response](#balance-interrupt-driven-work-and-incident-response)
   * [Application: Stabilization &amp; Operation](#application-stabilization--operation)
   * [Design Challenge #7: Monitoring &amp; Alerting](#design-challenge-7-monitoring--alerting)
      * [Business Challenge](#business-challenge)
      * [What monitoring and alerting to set up for the logs](#what-monitoring-and-alerting-to-set-up-for-the-logs)
      * [Google's reference architectures online](#googles-reference-architectures-online)
   * [Lab: Deployment Manager - Full Production](#lab-deployment-manager---full-production)
* [Resources/Articles](#resourcesarticles)



## Design for Resiliency, Scalability, and Disaster Recovery

Implement technologies and processes that assure business continuity in the event of a disaster.

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/pWlcV/design-for-resiliency-scalability-and-disaster-recovery-overview)

### Overview

This module deals with resiliency. The ability of a system to stay available and to bounce back from problems. But what is a resilient or available design? Is resiliency something you can add? Is it a feature you can turn on? Not really. Resiliency is the quality of a design that accounts for and handles failure. One principle of design is that sometimes a quality you want in the system isn't something you can really do anything about. To get the quality you want you have to look 180 degrees in the opposite direction. In this case, to get availability you have to look at and deal with the potential causes and sources of failure.

This module is designed for:

- **resiliency**,
- **scalability** and,
- **disaster recovery**.

<img src="../images/resiliency_definition.png"
     alt="resiliency_definition.png"
     style="float: left; margin-right: 10px;" />

we're gonna be covering failure; in general, failure due to a loss, failure due to overload. How do we cope with failure? Here, go through to a psychiatrist on that one. What about business continuity? How do we continue if there is a failure and disaster recovery? If there's something major, how do we recover completely from this? Then we will finally talk about scalable and resilient design, which is supposedly supposed to offset all of these bad things from happening or at least dealing with them at least. So then we're going to have an out-of-service issue with our photo service, and then we're going to have to redesign our logging system. 

### Failure Due to Loss

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/1RhEP/design-for-resiliency-scalability-and-disaster-recovery-failure-due-to-loss)

#### Failure is mandatory

For a period of time in the 1960s, a research team was trying to develop a perfect conductor. The theory was that if they could grow a perfect crystal and metal wire, there would be no signal loss and, therefore, no errors in communication. And they succeeded in creating the perfect wire. However, when they tested it, sometimes there were still errors. Do you know why? It's because we live in a quantum mechanical universe, and the location of electrons moving down a conductor is probabilistic. So, occasionally, an electron will appear outside of the wire and get lost. Errors are going to happen. Loss is going to happen.

> So the challenge isn't to avoid it, but to accept it and deal with it.

In this lesson, you'll learn about designing systems to handle failure caused by loss of resources.

<img src="../images/resiliency_failure_is_mandatory.png"
     alt="resiliency_failure_is_mandatory.png"
     style="float: left; margin-right: 10px;" />

#### Single Point of failure

<img src="../images/resiliency_failure_single_point_of_failure.png"
     alt="resiliency_failure_single_point_of_failure.png"
     style="float: left; margin-right: 10px;" />

#### Design to avoid Single Point of failure: N+2 (a spare spare)

<img src="../images/resiliency_failure_design_for_single_point_of_failure.png"
     alt="resiliency_failure_design_for_single_point_of_failure.png"
     style="float: left; margin-right: 10px;" />

#### Correlated failures

<img src="../images/resiliency_failure_correlated_failures.png"
     alt="resiliency_failure_correlated_failures.png"
     style="float: left; margin-right: 10px;" />

#### Design to avoid correlated failures

<img src="../images/resiliency_failure_design_to_avoid_correlated_failures.png"
     alt="resiliency_failure_design_to_avoid_correlated_failures.png"
     style="float: left; margin-right: 10px;" />


### Failure Due to Overload

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/LbKLf/design-for-resiliency-scalability-and-disaster-recovery-failure-due-to-overload)

When a system is overloaded at some point the system crosses over into nonlinear behavior. It can crash, thrash, stop responding or break adjacent resources at the service depends on. There's a very specific relationship between failure due to loss and failure due to overload. Imagine for example that a resource is lost and you queue up the work for that resource. All the work that comes in gets backlogged. When the resource is restored, there's this tremendous backlog of work to get done before any new work can be handled and if there's enough of it, nothing new ever gets done. So then the system goes from being totally unavailable due to resource loss, to totally unavailable due to overload. In this lesson you'll learn about the common causes of overload failure and how to plan for them and deal with them. When it comes to overload, prevention is really the best solution so design is critical.

<img src="../images/resiliency_failure_due_to_overload.png"
     alt="resiliency_failure_due_to_overload.png"
     style="float: left; margin-right: 10px;" />

#### Failover design for reliability

<img src="../images/resiliency_failure_due_to_overload_failover_design_for_reliability.png"
     alt="resiliency_failure_due_to_overload_failover_design_for_reliability.png"
     style="float: left; margin-right: 10px;" />

#### Cascading failures

<img src="../images/resiliency_failure_due_to_overload_cascading_failures.png"
     alt="resiliency_failure_due_to_overload_cascading_failures.png"
     style="float: left; margin-right: 10px;" />

#### Design to avoid Cascading failures

<img src="../images/resiliency_failure_due_to_overload_design_to_avoid_cascading_failures.png"
     alt="resiliency_failure_due_to_overload_design_to_avoid_cascading_failures.png"
     style="float: left; margin-right: 10px;" />

Example:

<img src="../images/resiliency_failure_due_to_overload_design_to_avoid_cascading_failures_example.png"
     alt="resiliency_failure_due_to_overload_design_to_avoid_cascading_failures_example.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/resiliency_failure_due_to_overload_design_to_avoid_cascading_failures_mitigate_incast_failure.png"
     alt="resiliency_failure_due_to_overload_design_to_avoid_cascading_failures_mitigate_incast_failure.png"
     style="float: left; margin-right: 10px;" />

#### Queries-of-Death overload failure

<img src="../images/resiliency_failure_due_to_overload_QueriesOfDeath_failures.png"
     alt="resiliency_failure_due_to_overload_QueriesOfDeath_failures.png"
     style="float: left; margin-right: 10px;" />

#### Positive feedback cycle overload failure

<img src="../images/resiliency_failure_due_to_overload_positive_feedback_overload_failures.png"
     alt="resiliency_failure_due_to_overload_positive_feedback_overload_failures.png"
     style="float: left; margin-right: 10px;" />

#### Detect overload early: Early warning systems (_canaries_)

<img src="../images/resiliency_failure_due_to_overload_detect_early_canaries.png"
     alt="resiliency_failure_due_to_overload_detect_early_canaries.png"
     style="float: left; margin-right: 10px;" />

### Coping with Failure

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/jm9LV/design-for-resiliency-scalability-and-disaster-recovery-coping-with-failure)


The time to prepare for an emergency is before it happens. Moreover, the way to prepare for failure is to embrace it, except that sooner or later, it's inevitable. By making the processes and behaviors you want part of the normal routine operations, you avoid the surprise.

For example, if you know that a zone outage is possible, consider establishing rotating outages as part of the routine operations. Here's another idea, if you know that the users expect 99.95 percent availability, and your service is operating at 99.99 percent availability, consider using that 0.04 percent gap to exercise your resiliency and recovery designs. Finally, don't underestimate the importance of meetings. Circumstances are going to change, if you surround the technical processes with the right human processes, the team will catch the issues before they become emergencies.

<img src="../images/resiliency_coping_with_failure.png"
     alt="resiliency_coping_with_failure.png"
     style="float: left; margin-right: 10px;" />


#### Forest fires or Controlled burns

<img src="../images/resiliency_coping_with_failure_forest_fire_or_controlled_burn.png"
     alt="resiliency_coping_with_failure_forest_fire_or_controlled_burn.png"
     style="float: left; margin-right: 10px;" />

#### Prepare the team

<img src="../images/resiliency_coping_with_failure_prepare_the_team.png"
     alt="resiliency_coping_with_failure_prepare_the_team.png"
     style="float: left; margin-right: 10px;" />

#### Incorporate failure into SLOs

<img src="../images/resiliency_coping_with_failure_include_in_SLOs.png"
     alt="resiliency_coping_with_failure_include_in_SLOs.png"
     style="float: left; margin-right: 10px;" />

#### Monthly meetings to build processes

<img src="../images/resiliency_coping_with_failure_meeting_monthly_meetings.png"
     alt="resiliency_coping_with_failure_meeting_monthly_meetings.png"
     style="float: left; margin-right: 10px;" />

#### Strategies for dealing with failure

<img src="../images/resiliency_coping_with_failure_strategies.png"
     alt="resiliency_coping_with_failure_strategies.png"
     style="float: left; margin-right: 10px;" />


### Business Continuity & Disaster Recovery

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/FYikQ/design-for-resiliency-scalability-and-disaster-recovery-business-continuity-and)

The overall strategy for business continuity can be summed up in this motto;

> No surprises.

Whatever's happening or could happen, you want to find out about it early and you want to give yourself plenty of recovery options in the design of your system. Now that's a balance.

How much resource and energy do you want to spend on insurance? You might have great recovery systems built into your design, but how do you know they're working, and how do you know that something hasn't changed and those systems haven't quietly stopped working? You need to understand what level of testing and exercise of the recovery systems gives you confidence. That will help you decide what to include in the design elements and also help shape the human processes that operate and maintain the system. 

<img src="../images/resiliency_business_continuity_disaster_recovery.png"
     alt="resiliency_business_continuity_disaster_recovery.png"
     style="float: left; margin-right: 10px;" />

#### Cloud DNS: 100% availability

<img src="../images/resiliency_business_continuity_disaster_recovery_CloudDNS.png"
     alt="resiliency_business_continuity_disaster_recovery_CloudDNS.png"
     style="float: left; margin-right: 10px;" />

#### Data Integrity

<img src="../images/resiliency_business_continuity_disaster_recovery_data_integrity.png"
     alt="resiliency_business_continuity_disaster_recovery_data_integrity.png"
     style="float: left; margin-right: 10px;" />

#### Reliable recovery with Lazy Deletion

<img src="../images/resiliency_business_continuity_disaster_recovery_lazy_or_soft_deletion.png"
     alt="resiliency_business_continuity_disaster_recovery_lazy_or_soft_deletion.png"
     style="float: left; margin-right: 10px;" />

#### backup, archive, RESTORE!

<img src="../images/resiliency_business_continuity_disaster_recovery_backup_archive_restore.png"
     alt="resiliency_business_continuity_disaster_recovery_backup_archive_restore.png"
     style="float: left; margin-right: 10px;" />

#### Tiered backup for resiliency

<img src="../images/resiliency_business_continuity_disaster_tiered_backup_services.png"
     alt="resiliency_business_continuity_disaster_tiered_backup_services.png"
     style="float: left; margin-right: 10px;" />

##### Cloud Storage features for backup and DR

<img src="../images/resiliency_business_continuity_disaster_tiered_backup_services_cloud_Storage.png"
     alt="resiliency_business_continuity_disaster_tiered_backup_services_cloud_Storage.png"
     style="float: left; margin-right: 10px;" />

#### Prepare the team for disasters

<img src="../images/resiliency_business_continuity_disaster_practice_document_prepare_the_team.png"
     alt="resiliency_business_continuity_disaster_practice_document_prepare_the_team.png"
     style="float: left; margin-right: 10px;" />


### Scalable & Resilient Design

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/E9vLK/design-for-resiliency-scalability-and-disaster-recovery-scalable-and-resilient) 

Vertical scaling makes components bigger, but it leaves them as a single point of failure. For example, swapping out a single VM for VM with larger capacity, still means that VM can fail and potentially crash your service. Horizontal scaling make services bigger through multiplicity. It leaves a unit capacity the same, but increases the pool of units. For example, instead of growing a larger VM, you could move to a design with a pool consisting of multiple smaller VMs. That not only makes it scalable, but resilient, because if one VM is lost, the others can pick up the workload until replacement is added. There are several steps you can take to make your design resilient, and they're covered in this lesson

1. **Health checks to monitor instances**

<img src="../images/resiliency_design_health_checks.png"
     alt="resiliency_design_health_checks.png"
     style="float: left; margin-right: 10px;" />

2. **Automatically replace instances**

<img src="../images/resiliency_design_auto_replace_instances.png"
     alt="resiliency_design_auto_replace_instances.png"
     style="float: left; margin-right: 10px;" />

3. Resilient Storage: Cloud Storage, Cloud SQL

<img src="../images/resiliency_design_resilient_storage.png"
     alt="resiliency_design_resilient_storage.png"
     style="float: left; margin-right: 10px;" />

4. Resilient Network

<img src="../images/resiliency_design_resilient_network.png"
     alt="resiliency_design_resilient_network.png"
     style="float: left; margin-right: 10px;" />

#### Design pattern: General design for scalable & resilient apps

<img src="../images/resiliency_design_design_pattern_general_design_for_scalable_resilient_apps.png"
     alt="resiliency_design_design_pattern_general_design_for_scalable_resilient_apps.png"
     style="float: left; margin-right: 10px;" />


* Handles **loss of instance**

<img src="../images/general_design_for_scalable_resilient_apps_loss_of_instance.png"
     alt="general_design_for_scalable_resilient_apps_loss_of_instance.png"
     style="float: left; margin-right: 10px;" />

* Handles **loss of zone**

<img src="../images/general_design_for_scalable_resilient_apps_loss_of_zone.png"
     alt="general_design_for_scalable_resilient_apps_loss_of_zone.png"
     style="float: left; margin-right: 10px;" />

* Handles **loss of database**

<img src="../images/general_design_for_scalable_resilient_apps_loss_of_database.png"
     alt="general_design_for_scalable_resilient_apps_loss_of_database.png"
     style="float: left; margin-right: 10px;" />

* Handles **full disaster recovery**

<img src="../images/general_design_for_scalable_resilient_apps_full_disaster_recovery.png"
     alt="general_design_for_scalable_resilient_apps_full_disaster_recovery.png"
     style="float: left; margin-right: 10px;" />

#### Microservices design for scalable & resilient streaming

<img src="../images/resiliency_design_design_pattern_microservices_design.png"
     alt="resiliency_design_design_pattern_microservices_design.png"
     style="float: left; margin-right: 10px;" />

#### 12-factor system & application design in GCP

<img src="../images/resiliency_design_design_pattern_12-factor_design.png"
     alt="resiliency_design_design_pattern_12-factor_design.png"
     style="float: left; margin-right: 10px;" />

#### Processes for simple, iterative, aligned development

<img src="../images/resiliency_design_processes.png"
     alt="resiliency_design_processes.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/resiliency_design_processes_iterate.png"
     alt="resiliency_design_processes_iterate.png"
     style="float: left; margin-right: 10px;" />

This module covered several related design goals, including:

* reliability,
* scalability,
* and disaster recovery.

The first subject was availability and reliability. A key concept is that planning for failure and dealing with failure in your design leads to improved reliability. Failure can occur due to the loss of a resource or it can occur due to overload. You must be careful when making adjustments to a system, that you don't accidentally create the potential for an overload failure when you're trying to improve resiliency to a loss failure. The second subject was disaster recovery. You learned that planning for disaster and preparing for recovery is key. The third was scalable and resilient design. That brings together many of the design principles you've seen in the previous modules, and shows how they all fit together into a general resilient solution.


### Application: Out of Service!

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/SeWZH/out-of-service) 

#### Business problem

It's a **Design problem**, we lost an entire zone!!!

<img src="../images/application_photo_Service_crashed.png"
     alt="application_photo_Service_crashed.png"
     style="float: left; margin-right: 10px;" />

The popular and growing photo services suddenly crashed:

* How do you handle a major outage?
* What could the cause be? What changes can you make the design so this problem doesn't take down the entire service again in the future?

<img src="../images/application_photo_Service_crashed_problem.png"
     alt="application_photo_Service_crashed_problem.png"
     style="float: left; margin-right: 10px;" />


**Have a plan for dealing with a major outage**

<img src="../images/application_photo_Service_crashed_solution_have_process_in_place.png"
     alt="application_photo_Service_crashed_solution_have_process_in_place.png"
     style="float: left; margin-right: 10px;" />


#### Systematic logical troubleshooting

**Service loss due to zone outage**

<img src="../images/application_photo_Service_crashed_troubleshooting.png"
     alt="application_photo_Service_crashed_troubleshooting.png"
     style="float: left; margin-right: 10px;" />


#### Collaboration & communication: Report, Document, build policy

So you want to **move these servers to multiple zones.**

<img src="../images/application_photo_Service_crashed_solution_multiple_zones.png"
     alt="application_photo_Service_crashed_solution_multiple_zones.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/dummy.png"
     alt="dummy.png"
     style="float: left; margin-right: 10px;" />
<img src="../images/dummy.png"
     alt="dummy.png"
     style="float: left; margin-right: 10px;" />
<img src="../images/dummy.png"
     alt="dummy.png"
     style="float: left; margin-right: 10px;" />


#### Break down business logic on the photo service

#### What about our Service Level Objectives (SLOs) and Indicators (SLIs)

SLOs didn't change again. We just added more redundancy, making the service span multiple zones.


<img src="../images/application_photo_Service_crashed_SLOs.png"
     alt="application_photo_Service_crashed_SLOs.png"
     style="float: left; margin-right: 10px;" />


### Design Challenge #4: Redesign for Time



<img src="../images/application_photo_Service_crashed_again_SinglePointOfFAilure.png"
     alt="application_photo_Service_crashed_again_SinglePointOfFAilure.png"
     style="float: left; margin-right: 10px;" />


**Need to scale frontend server**

<img src="../images/application_photo_Service_crashed_again_solution_scale_upload_servers_Across_zones.png"
     alt="application_photo_Service_crashed_again_solution_scale_upload_servers_Across_zones.png"
     style="float: left; margin-right: 10px;" />

**Prevent overload: MAke load testing real**

<img src="../images/application_photo_Service_crashed_again_prevent_overload_with_real_testing.png"
     alt="application_photo_Service_crashed_again_prevent_overload_with_real_testing.png"
     style="float: left; margin-right: 10px;" />

**Scaling requires breaking state out of the upload server**

<img src="../images/application_photo_Service_crashed_again_scale_upload_server_stateless.png"
     alt="application_photo_Service_crashed_again_scale_upload_server_stateless.png"
     style="float: left; margin-right: 10px;" />


What does that look like?

**Need to make Frontend servers stateless**

<img src="../images/application_photo_Service_crashed_again_scale_upload_server_stateless_how.png"
     alt="application_photo_Service_crashed_again_scale_upload_server_stateless_how.png"
     style="float: left; margin-right: 10px;" />

**Update on SLOs and SLIs**

You see what it is that you can measure and then quantify it.

<img src="../images/application_photo_Service_crashed_again_new_SLOs.png"
     alt="application_photo_Service_crashed_again_new_SLOs.png"
     style="float: left; margin-right: 10px;" />


#### Design Challenge: Log aggregation delayed troubleshooting

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/9EsdO/design-challenge-4-redesign-for-time)

When the photo service crashed, it became evident that troubleshooting was taking too long. The reason for the delay was tracked to log aggregation. The aggregated logs needed for troubleshooting were delayed. Worse, the more problems that are occurring in the system, the more log entries are generated and the longer it takes for the aggregated logs to become available for troubleshooting. Can you redesign the log system to eliminate the bottlenecks? Watch the lesson that describes the problem, then come up with your own solution. When you're ready, continue the lesson to see a sample solution.

<img src="../images/design_challenge_redesign_for_time.png"
     alt="design_challenge_redesign_for_time.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/design_challenge_redesign_for_time_problem.png"
     alt="design_challenge_redesign_for_time_problem.png"
     style="float: left; margin-right: 10px;" />

If you remember the **12-factor design**, it says to **treat log events as streams** so that should be a clue. The business issue is servant's service resiliency. It's just taking too long to troubleshoot service issues, batch processing of the logs, just simply does not support live service troubleshooting. It's causing delays, we can't meet our service level objectives, we can't identify and respond to incidents in times. So here's the design challenge. Replace the cron batch processing with stream processing and here's our hint. Try to consider a microservices design.


<img src="../images/design_challenge_redesign_for_time_challenge.png"
     alt="design_challenge_redesign_for_time_challenge.png"
     style="float: left; margin-right: 10px;" />

#### Troubleshooting & solution

<img src="../images/design_challenge_redesign_for_time_troubleshooting.png"
     alt="design_challenge_redesign_for_time_troubleshooting.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/design_challenge_redesign_for_time_solution.png"
     alt="design_challenge_redesign_for_time_solution.png"
     style="float: left; margin-right: 10px;" />

Instead of having a cronjob, we have not converted it to Stream Processing with Cloud Pub/Sub.





## Design for Security

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/bNzDv/design-for-security-overview)

Implement policies that minimize security risks, such as auditing, separation of duties and least privilege.

### Overview

There are **3 kinds of security services** built into the Google Cloud platform: 
1. services that are **transparent and automatic**, such as encryption of data that occurs automatically when data's transported and when it's at rest.
2. services that have **defaults but that offer methods for customizations**, such as using your own encryption keys rather than those provided.
3. services that can be used as part of your security design, but only contribute to security if you choose to use them in your design.

<img src="../images/security_overview.png"
     alt="security_overview.png"
     style="float: left; margin-right: 10px;" />

### Cloud Security

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/wMJ6H/design-for-security-cloud-security)

When you migrate an application to the cloud or develop an application in the cloud, there are security benefits that the application inherits simply because of the host environment. Google already has to protect its applications, and many of the benefits of that security effort are built into the infrastructure itself. You need to know about them so you don't accidentally spend effort duplicating them. You also need to know where those services end and your security design begins so that you don't accidentally leave gaps in your security strategy.

#### Google's strategy for cloud security: "Pervasive efense in depth"

<img src="../images/security_Google_strategy.png"
     alt="security_Google_strategy.png"
     style="float: left; margin-right: 10px;" />

#### Cloud Networking Security: Defense in Depth

"So the least that we can actually expose to the Internet, all the better"

<img src="../images/security_Google_defense_in_depth.png"
     alt="security_Google_defense_in_depth.png"
     style="float: left; margin-right: 10px;" />

### Network Access Control & Firewalls

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/tx88k/design-for-security-network-access-control-and-firewalls)

The first level of security where your design can have a significant impact is on network level access control. For example, if you remove the external IP from an instance in a bastion hosts design, you'll eliminate one target that could be attacked. Locking down network access to only what's required is one way to reduce the potential attack surface. 

#### Firewall configuration: 1st line of defense for access

<img src="../images/security_firewalls.png"
     alt="security_firewalls.png"
     style="float: left; margin-right: 10px;" />

#### Design for securely accessing VMs

<img src="../images/security_secure_VMs.png"
     alt="security_secure_VMs.png"
     style="float: left; margin-right: 10px;" />

#### API access control with Cloud Endpoints

<img src="../images/security_API_control_with_Cloud_Endpoint.png"
     alt="security_API_control_with_Cloud_Endpoint.png"
     style="float: left; margin-right: 10px;" />

### Protections Against Denial of Service

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/9I9iK/design-for-security-protections-against-denial-of-service)

Part of the protections against denial of service attacks are built into the cloud infrastructure. The network, for example, uses software defined networking or SDN. Since there are no physical routers and no physical load balancers, there are no actual hardware interfaces that could be overloaded. There are also services that adapt to demand in intelligent ways, and you can use these in your design to afford further protection against overload attacks

<img src="../images/security_DDOS.png"
     alt="security_DDOS.png"
     style="float: left; margin-right: 10px;" />

#### Edge protections agaisnt DDoS

<img src="../images/security_protection_vs_DDOS.png"
     alt="security_protection_vs_DDOS.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/security_protection_vs_DDOS_with_network.png"
     alt="security_protection_vs_DDOS_with_network.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/security_infrastructure_protection_vs_DDOS.png"
     alt="security_infrastructure_protection_vs_DDOS.png"
     style="float: left; margin-right: 10px;" />

### Resource Sharing & Isolation... a compromise

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/vUZeS/design-for-security-resource-sharing-and-isolation)

Google Cloud Platform provides a rich array of network topology features, that provide different blends of separation isolation, and communication, and sharing. The least secure design is where everything is in a single failure domain, and all the parts communicate and depend directly on one another. There are many ways of separating those parts and providing more private, or tolerant communication channels between them, creating multiple failure domains and therefore better isolation. In submarine design, the parts of the submarine are divided into compartments that can be sealed off from one another. This helps with reliability, because one compartment can flood and be sealed off from the rest. But it also helps with security, because if an attacker gains entry to one compartment, it can be sealed off to limit the damage.

<img src="../images/security_resource_sharing_def.png"
     alt="security_resource_sharing_def.png"
     style="float: left; margin-right: 10px;" />

#### VPC isolation through public IPs

<img src="../images/security_resource_sharing_VPC_isolations_through_public_IPs.png"
     alt="security_resource_sharing_VPC_isolations_through_public_IPs.png"
     style="float: left; margin-right: 10px;" />

#### IP address isolation using VPN tunneling

<img src="../images/security_resource_sharing_IP_isolations_through_VPN.png"
     alt="security_resource_sharing_IP_isolations_through_VPN.png"
     style="float: left; margin-right: 10px;" />

#### Cross-project VPC network peering

<img src="../images/security_resource_cross_project.png"
     alt="security_resource_cross_project.png"
     style="float: left; margin-right: 10px;" />

#### Cross-organization VPC network peering

<img src="../images/security_resource_cross_organization_sharing.png"
     alt="security_resource_cross_organization_sharing.png"
     style="float: left; margin-right: 10px;" />

#### Shared VPC

<img src="../images/security_resource_VPC_sharing.png"
     alt="security_resource_VPC_sharing.png"
     style="float: left; margin-right: 10px;" />

#### Isolation through multiple network interface

<img src="../images/security_resource_multi_NIC.png"
     alt="security_resource_multi_NIC.png"
     style="float: left; margin-right: 10px;" />

#### Access GCP services over internal IP

<img src="../images/security_resource_GCP_over_internal_IP.png"
     alt="security_resource_GCP_over_internal_IP.png"
     style="float: left; margin-right: 10px;" />


### Data Encryption & Key Management

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/m1739/design-for-security-data-encryption-and-key-management)

You probably already know that Google automatically encrypts data in motion and data at rest, but that description generalizes some of the details that will help you make design decisions. For example, you can use Google's built-in key management, or you can provide your own keys. Also for particularly sensitive data, you can add your own encryption methods in addition to those provided


<img src="../images/security_encryption_all_data_in_motion_at_rest_encrypted.png"
     alt="security_encryption_all_data_in_motion_at_rest_encrypted.png"
     style="float: left; margin-right: 10px;" />

#### Server-side encryption

<img src="../images/security_encryption.png"
     alt="security_encryption.png"
     style="float: left; margin-right: 10px;" />

#### Customer manager encryption keys (CMEK)

<img src="../images/security_custom_encryption_keys.png"
     alt="security_custom_encryption_keys.png"
     style="float: left; margin-right: 10px;" />

#### Customer Supplied encryption keys (CSEK)

<img src="../images/security_custom_supplied_encryption_keys.png"
     alt="security_custom_supplied_encryption_keys.png"
     style="float: left; margin-right: 10px;" />

#### Persistent Disk Encrytion with CSEK

<img src="../images/security_persistent_disk_CSEK.png"
     alt="security_persistent_disk_CSEK.png"
     style="float: left; margin-right: 10px;" />

#### Moore control over encryption

<img src="../images/security_encryption_more_control.png"
     alt="security_encryption_more_control.png"
     style="float: left; margin-right: 10px;" />

### Design for Security: Identity Access & Auditing

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/k0FDO/design-for-security-identity-access-and-auditing)

Authorization, access to resources is controlled by Google's Identity and Access Management or IAM system. You're already using this service to control authorized access. By using the auditing tools available, you can also check for unwanted actions like attempts at unauthorized access. That can tell you where the attackers interest is focused. So you can add security measures in those areas. 

#### Identity Access Management

<img src="../images/security_IAM.png"
     alt="security_IAM.png"
     style="float: left; margin-right: 10px;" />

#### Service Accounts

<img src="../images/security_Service_Account.png"
     alt="security_Service_Account.png"
     style="float: left; margin-right: 10px;" />

#### GCP security auditing with Forseti-security (Open Source)

<img src="../images/security_GCP_Security_Auditing_wth_Forseti.png"
     alt="security_GCP_Security_Auditing_wth_Forseti.png"
     style="float: left; margin-right: 10px;" />

#### Cloud Audit Logging

<img src="../images/security_Cloud_Audit_Logging.png"
     alt="security_Cloud_Audit_Logging.png"
     style="float: left; margin-right: 10px;" />

#### External audits & GCP Standards Compliance


<img src="../images/security_Standard_Compliance.png"
     alt="security_Standard_Compliance.png"
     style="float: left; margin-right: 10px;" />

This module covered security from several perspectives, including identity and access management, data encryption and key management, resource sharing and isolation for compartmentalization, protections against denial of service attacks, network access control, and the automatic protections built into the platform and services. You learn that there are some security that's inherited from the environment. Some is configured with default options that you might want to change, and some security features are optional and can be included in your design, if it makes sense with your security strategy.

### Application: Photo Service - Intentional Attack

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/dwTwf/photo-service-intentional-attack)

There's evidence that hackers are trying to compromise the private information of system users, and maybe try to bring down the service.

That brings up 2 important issues:
1. How does the system keep users data private?
2. How does the system protect against a denial-of-service attack?

Identify the protections already in place that are provided by the platform by default, then consider additional design changes that could provide additional protections.

<img src="../images/application_photo_Service_intentional_attack.png"
     alt="application_photo_Service_intentional_attack.png"
     style="float: left; margin-right: 10px;" />

#### Business problem

<img src="../images/application_photo_Service_intentional_attack_business_problem.png"
     alt="application_photo_Service_intentional_attack_business_problem.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/application_photo_Service_intentional_attack_business_problem_architecture.png"
     alt="application_photo_Service_intentional_attack_business_problem_architecture.png"
     style="float: left; margin-right: 10px;" />



#### Break down business logic on the photo service

**Lock down the frontend**

<img src="../images/application_photo_Service_intentional_attack_business_problem_solution.png"
     alt="application_photo_Service_intentional_attack_business_problem_solution.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/application_photo_Service_intentional_attack_business_process_if_DDoS.png"
     alt="application_photo_Service_intentional_attack_business_process_if_DDoS.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/application_photo_Service_intentional_attack_business_actions_vs_DDoS.png"
     alt="application_photo_Service_intentional_attack_business_actions_vs_DDoS.png"
     style="float: left; margin-right: 10px;" />

1. use Cloud CDN to cache our thumbnails accross the world
2. use Cloud DNS 
3. Implement auto-scaling (instance group)

**Can we protect the backend?**

<img src="../images/application_photo_Service_intentional_attack_backend.png"
     alt="application_photo_Service_intentional_attack_backend.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/application_photo_Service_intentional_attack_backend_lockdown_VPC.png"
     alt="application_photo_Service_intentional_attack_backend_lockdown_VPC.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/application_photo_Service_intentional_attack_backend_lockdown_Private_network.png"
     alt="application_photo_Service_intentional_attack_backend_lockdown_Private_network.png"
     style="float: left; margin-right: 10px;" />

#### Security checklist

<img src="../images/application_photo_Service_intentional_attack_security_checklist.png"
     alt="application_photo_Service_intentional_attack_security_checklist.png"
     style="float: left; margin-right: 10px;" />


### Design Challenge #5: Defense in Depth

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/vVI8A/design-challenge-5-defense-in-depth)

The security measures you're considering implementing in the photo service will make the system much more secure. But wait a moment, the user information and event information may be contained in the logs. If the log system isn't secure, none of the rest of the system is secure. Watch the lesson that describes the problem, then come up with your own solution. When you're ready, continue the lesson to see a sample solution, and remember that the sample solution is not the best possible solution. It's just an example.


<img src="../images/design_challenge_security_log_files.png"
     alt="design_challenge_security_log_files.png"
     style="float: left; margin-right: 10px;" />

**Problem**

<img src="../images/design_challenge_security_log_files_problem.png"
     alt="design_challenge_security_log_files_problem.png"
     style="float: left; margin-right: 10px;" />

**Possible solution**

<img src="../images/design_challenge_security_log_files_solution.png"
     alt="design_challenge_security_log_files_solution.png"
     style="float: left; margin-right: 10px;" />

## Capacity Planning & Cost Optimization

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/SsEgy/capacity-planning-and-cost-optimization-overview)

Identify ways to optimize resources and minimize cost.

### Overview

Both forecasting for future demand on a system, and planning the resources for a system, depend on non-abstract large-scale design sometimes called dimensioning.

When you optimize for one factor by changing a resource, there may be other consequences. For example, if you change the VM size to optimize CPU capacity, it's possible that network throughput memory and disk capacity could change as a consequence. So, you really need to think through all the dimensions that are affected by your design and perform the calculations to ensure there's sufficient capacity for your purposes.

A common mistake is to optimize away resiliency. Remember that overcapacity is sometimes included by design to handle bursty periods, growth, or intentional attacks. Failing to recognize the purpose of excess capacity, and then reducing it to save money, can create opportunities for cascade failures.

<img src="../images/dimensioning_capacity_planning_pricing.png"
     alt="dimensioning_capacity_planning_pricing.png"
     style="float: left; margin-right: 10px;" />

### Capacity Planning

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/0h7MF/capacity-planning-and-cost-optimization-capacity-planning)

Capacity planning is **an ongoing cyclical process**.

There are various common measures such as:

* VM instance capacity,
* disk performance,
* network throughput,
* and workload estimations.

Ultimately, you need to be able to answer the question, **is there sufficient resource with reasonable certainty?** One of the key design principles in this course is to allow other factors to influence your design first, and then come back and dimension the design later. You might have to change some of the design for capacity or for better pricing, but at least, you'll make these adjustments knowing what benefits you're trading for reduced cost or better capacity management.

**Capacity planning cycle:**

<img src="../images/dimensioning_cycle.png"
     alt="dimensioning_cycle.png"
     style="float: left; margin-right: 10px;" />

#### 1. Forecast

<img src="../images/dimensioning_cycle_forecast.png"
     alt="dimensioning_cycle_forecast.png"
     style="float: left; margin-right: 10px;" />

##### Forecast estimation

<img src="../images/dimensioning_cycle_forecast_estimation.png"
     alt="dimensioning_cycle_forecast_estimation.png"
     style="float: left; margin-right: 10px;" />


##### Instance overhead estimation

How to NOT overestimate:

<img src="../images/dimensioning_cycle_forecast_instance_overhead_estimation.png"
     alt="dimensioning_cycle_forecast_instance_overhead_estimation.png"
     style="float: left; margin-right: 10px;" />

##### Persistent disks estimation

<img src="../images/dimensioning_cycle_forecast_presistence_disks_estimation.png"
     alt="dimensioning_cycle_forecast_presistence_disks_estimation.png"
     style="float: left; margin-right: 10px;" />


##### Network capacity estimation

<img src="../images/dimensioning_cycle_forecast_network_estimation.png"
     alt="dimensioning_cycle_forecast_network_estimation.png"
     style="float: left; margin-right: 10px;" />

##### Workload estimation

<img src="../images/dimensioning_cycle_forecast_workload_estimation.png"
     alt="dimensioning_cycle_forecast_workload_estimation.png"
     style="float: left; margin-right: 10px;" />

[**Perfkit Benchmarker**](https://github.com/GoogleCloudPlatform/PerfKitBenchmarker) (Open source tool by Google)



<img src="../images/dimensioning_cycle_forecast_workload_estimation_PerfkitBEnchmarker.png"
     alt="dimensioning_cycle_forecast_workload_estimation_PerfkitBEnchmarker.png"
     style="float: left; margin-right: 10px;" />

#### Allocate

<img src="../images/dimensioning_cycle_allocate.png"
     alt="dimensioning_cycle_allocate.png"
     style="float: left; margin-right: 10px;" />

Example with rough estimation:

<img src="../images/dimensioning_cycle_allocate_example.png"
     alt="dimensioning_cycle_allocate_example.png"
     style="float: left; margin-right: 10px;" />

Opportunity for optimization before allocating more resources?

<img src="../images/dimensioning_cycle_allocate_opportunity_for_optimization.png"
     alt="dimensioning_cycle_allocate_opportunity_for_optimization.png"
     style="float: left; margin-right: 10px;" />

#### Approve

<img src="../images/dimensioning_cycle_approve.png"
     alt="dimensioning_cycle_approve.png"
     style="float: left; margin-right: 10px;" />

#### Deploy

First: Test, test, test...

<img src="../images/dimensioning_cycle_deploy.png"
     alt="dimensioning_cycle_deploy.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/dimensioning_balanced_approach_to_dimensioning.png"
     alt="dimensioning_balanced_approach_to_dimensioning.png"
     style="float: left; margin-right: 10px;" />



### Pricing

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/cwllj/capacity-planning-and-cost-optimization-pricing)

Pricing is commonly used in:

* **cost optimization**,
* **reducing cost**, 
* and also for **budgeting**.

One feature of Google Cloud Platform is that bulk use discounting is built in an automatic for many services. In this lesson, you'll learn about how design choices can influence price.

For example, you may have distributed an element of your solution over multiple regions to improve reliability. However, that distribution design might result in additional network charges for egress traffic. Is the cost of the reliability worthy additional network charges? Pricing estimation, and pricing that follows capacity planning can help you decide.

#### Optimize VMs cost

<img src="../images/pricing_optimize_VM_cost.png"
     alt="pricing_optimize_VM_cost.png"
     style="float: left; margin-right: 10px;" />

#### Optimize Disks cost

<img src="../images/pricing_optimize_disks_cost.png"
     alt="pricing_optimize_disks_cost.png"
     style="float: left; margin-right: 10px;" />

#### Optimize Network cost

<img src="../images/pricing_optimize_network_cost.png"
     alt="pricing_optimize_network_cost.png"
     style="float: left; margin-right: 10px;" />

VM to VM in the same zone:

<img src="../images/pricing_optimize_network_cost_same_zone_VM-to-VM.png"
     alt="pricing_optimize_network_cost_same_zone_VM-to-VM.png"
     style="float: left; margin-right: 10px;" />

In this module, you learned about capacity planning, including the planning cycle, and you learned about pricing. The two of them together, capacity and pricing, provide another perspective on design options. You can modify the design for cost optimization or to limit resource usage. One important point is to apply dimensioning to your design after you've considered other functional aspects of the design.


### Application: Photo Service - Cost & Capacity

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/E42DE/photo-service-cost-and-capacity)

Capacity planning for the coming year's completed.

As a final step, you'll look at the VM options and perform non-abstract **cost optimization analysis**.

Given the growing capacity requirements, what makes sense financially to choose for the most cost-effective?:

* a **bigger capacity VM**, 
* or is **sticking with the current size VM**

Can we offer the same service with less money?

<img src="../images/application_photo_Servicecost_optimization.png"
     alt="application_photo_Servicecost_optimization.png"
     style="float: left; margin-right: 10px;" />

#### Business problem

<img src="../images/application_photo_Service_budget.png"
     alt="application_photo_Service_budget.png"
     style="float: left; margin-right: 10px;" />

Reviewing the current architecture:

<img src="../images/application_photo_Service_review_archtecture.png"
     alt="application_photo_Service_review_archtecture.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/application_photo_Service_cost_optimization_problem.png"
     alt="application_photo_Service_cost_optimization_problem.png"
     style="float: left; margin-right: 10px;" />

We want to make a recommendation: **Should we move to higher cores CPUs?**.7

We first need to **check cost effectiveness**.

<img src="../images/application_photo_Service_check_cost_effectiveness.png"
     alt="application_photo_Service_check_cost_effectiveness.png"
     style="float: left; margin-right: 10px;" />


### Design Challenge #6: Dimensioning

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/MyV6T/design-challenge-6-dimensioning)

The photo application service design is now set to auto scale and grow for the projected doubling of demand in the coming year.

**However, that means the log information will also double**. The current storage service is Bigtable.

* Will the additional demand both data and traffic put stresses on Bigtable?
* Will the system need an additional Bigtable node to handle the demand in the coming year?

Watch the lesson that describes the problem then come up with your own solution, and when you're ready, continue the lesson to see a sample solution.

Current layout of our log service:

<img src="../images/design_challenge_capacity_planning_growth_logs.png"
     alt="design_challenge_capacity_planning_growth_logs.png"
     style="float: left; margin-right: 10px;" />

#### Growth status for BigTable

<img src="../images/design_challenge_capacity_planning_growth_logs_BigTable.png"
     alt="design_challenge_capacity_planning_growth_logs_BigTable.png"
     style="float: left; margin-right: 10px;" />

What can handle a BigTable node, in nb. of queries (qps), in throughput (MB/s)?

Our current use of BigTable:


<img src="../images/design_challenge_capacity_planning_BigTable_current_use.png"
     alt="design_challenge_capacity_planning_BigTable_current_use.png"
     style="float: left; margin-right: 10px;" />

- the size of the log payload for each of our workloads (web, app, data): ~552 B
- estimation of log entries per day: ~300 millions entries per day

Our system handles **~154.2 GB/day**, i.e. **~55TB/year**.


**What our service would look like if the usage double inthe coming year?**

<img src="../images/design_challenge_capacity_planning_BigTable_challenge.png"
     alt="design_challenge_capacity_planning_BigTable_challenge.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/design_challenge_capacity_planning_BigTable_estimate_growing_capacity.png"
     alt="design_challenge_capacity_planning_BigTable_estimate_growing_capacity.png"
     style="float: left; margin-right: 10px;" />

a BigTable node can handle up to 10 000 qps and 10MB/s of throughput. So doubling the usage of our app can be handled by a single BigTable node, but we need to consider our **storage capacity** reaching 110TB by the end of the 2nd year.

Doing the math, 22 BigTable servers using SSD drives won't be sufficient for the double growth forecasted for the coming year.

<img src="../images/design_challenge_capacity_planning_BigTable_estimate_growing_pricing.png"
     alt="design_challenge_capacity_planning_BigTable_estimate_growing_pricing.png"
     style="float: left; margin-right: 10px;" />


## Deployment, Monitoring and Alerting, and Incident Response

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/OFVf0/deployment-monitoring-and-alerting-and-incident-response-overview)

This module discusses **deploying, operating and maintaining your design**.

One of the things that's been visited repeatedly during this course, is that for a system to stabilize after implementation, it needs to be surrounded by properly prepared and designed behaviors.

What people do while operating and maintaining the system matters. The SLOs and SLIs you've been evolving through the design process, provide an objective method to manage the solution, to keep it running and on track. However, these same measures and the discipline of iteratively reviewing them, will also help determine when the circumstances have changed, when the assumptions of the original design are no longer true or accurate, and it's time to revisit the design and evolve the system.

> This module focuses on the behavioral part of your design.

<img src="../images/design_behavior_design_operations.png"
     alt="design_behavior_design_operations.png"
     style="float: left; margin-right: 10px;" />




### Learning Objectives

* Implement processes that minimize downtime, such as monitoring and alarming, unit and integration testing, production resilience testing, and incident post-mortem analysis.
* Launch a cloud service from a collection of templates.
* Configure basic black box monitoring of an application.
* Create an uptime check to recognize a loss of service.
* Establish an alerting policy to trigger incident response procedures.
* Create and configure a dashboard with dynamically update charts.
* Test the monitoring and alerting regimen by applying a load to the service.
* Test the monitoring and alerting regimen by simulating a service outage.

### Deployment

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/5imlo/deployment-monitoring-and-alerting-and-incident-response-deployment)

In this lesson, you'll learn some tips about how to deploy your solution. The advice seems like common sense. Make:

* a checklist,
* automate processes,
* use an infrastructure orchestration framework.

But don't underestimate the importance of these activities. They're at the core of deploying a stable solution.

1. Plan your checklist of dependencies for deployment

<img src="../images/design_behavior_deployment_plan.png"
     alt="design_behavior_deployment_plan.png"
     style="float: left; margin-right: 10px;" />

2. Launch automation with resilience in mind

<img src="../images/design_behavior_deployment_implement_automation.png"
     alt="design_behavior_deployment_implement_automation.png"
     style="float: left; margin-right: 10px;" />

Tool of choice: **Deployment Manager**

* configuration
* Resources
* Templates

<img src="../images/design_behavior_deployment_implement_automation_tool.png"
     alt="design_behavior_deployment_implement_automation_tool.png"
     style="float: left; margin-right: 10px;" />

### Monitoring & Alerting

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/WBkXI/deployment-monitoring-and-alerting-and-incident-response-monitoring-and-alerting)


This lesson covers:

* **monitoring and alerting** its concepts.
* It then **illustrates the application of these concepts with a stack driver service** including the kinds of monitoring that can be configured.
* **How to set up an alert and notification?**
* and **how to create a dashboard with charts to help visualize the running system?**

#### SRE pyramid: Monitoring is measuring

(https://landing.google.com/sre/books/)

<img src="../images/design_behavior_monitoring_is_measuring.png"
     alt="design_behavior_monitoring_is_measuring.png"
     style="float: left; margin-right: 10px;" />

#### Push-based and Pull-based metrics

<img src="../images/design_behavior_monitoring_push-based_pull-based_metrics.png"
     alt="design_behavior_monitoring_push-based_pull-based_metrics.png"
     style="float: left; margin-right: 10px;" />

#### Black box monitoring (affecting user experience)

<img src="../images/design_behavior_monitoring_blackbox.png"
     alt="design_behavior_monitoring_blackbox.png"
     style="float: left; margin-right: 10px;" />

#### White box monitoring (monitoring services)

<img src="../images/design_behavior_monitoring_whitebox.png"
     alt="design_behavior_monitoring_whitebox.png"
     style="float: left; margin-right: 10px;" />

#### Carefully output of monitoring systems: alerts, 

* **Alerts**: a human must take action immediately
* **Tickets**: a human must take action, but the situation isn't yet urgent
* **Logging**: diagnostic information only

<img src="../images/design_behavior_monitoring_output_carefuly.png"
     alt="design_behavior_monitoring_output_carefuly.png"
     style="float: left; margin-right: 10px;" />

#### 12-factor administration & operation in GCP: Stack driver

<img src="../images/design_behavior_monitoring_on_GCP.png"
     alt="design_behavior_monitoring_on_GCP.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/design_behavior_Stackdriver_unified_tool.png"
     alt="design_behavior_Stackdriver_unified_tool.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/design_behavior_Stackdriver_built_for_AWS.png"
     alt="design_behavior_Stackdriver_built_for_AWS.png"
     style="float: left; margin-right: 10px;" />

> Specify a specific Stackdriver account to make use of its services!

#### Some features of Stack driver

**Uptime (health) check details**

<img src="../images/design_behavior_Stackdriver_uptime_check.png"
     alt="design_behavior_Stackdriver_uptime_check.png"
     style="float: left; margin-right: 10px;" />

**Create alerts** (conditions, notifications, documentation)

<img src="../images/design_behavior_Stackdriver_create_alerts.png"
     alt="design_behavior_Stackdriver_create_alerts.png"
     style="float: left; margin-right: 10px;" />

**Dashboards**

<img src="../images/design_behavior_Stackdriver_create_dashboards.png"
     alt="design_behavior_Stackdriver_create_dashboards.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/design_behavior_Stackdriver_create_dashboards_dynamic.png"
     alt="design_behavior_Stackdriver_create_dashboards_dynamic.png"
     style="float: left; margin-right: 10px;" />

**Logging Agents** can be installed to capture all types of logs from other tiers too.

<img src="../images/design_behavior_Stackdriver_install_log_agents_also_for_tiers_products.png"
     alt="design_behavior_Stackdriver_install_log_agents_also_for_tiers_products.png"
     style="float: left; margin-right: 10px;" />


### Incident Response

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/7BevS/deployment-monitoring-and-alerting-and-incident-response-incident-response)

Incident response is **the human behavior that results in system stability when things don't go as planned**.

The Site Reliability Engineering or SRE model is introduced (see [references section](#resourcesarticles)). You've actually been learning best practices throughout this course that relate directly to the layers of the SRE model. By developing your design with reliability in mind you've established processes for operating, maintaining, and recovering system in the event that things start to go sideways. In this lesson you'll review the items that were discussed in detail earlier in the class to prepare for successful incident response. Now, we'll discuss a few final steps such as developing playbooks to implement the response strategy.


<img src="../images/incident_response_user_trust.png"
     alt="incident_response_user_trust.png"
     style="float: left; margin-right: 10px;" />

#### Structured incident response

<img src="../images/incident_response_structure.png"
     alt="incident_response_structure.png"
     style="float: left; margin-right: 10px;" />
     
It includes:

* Monitoring dashboards
* Alterting regimen
* Plans & Tools for responding to issues

<img src="../images/incident_response_structure_details.png"
     alt="incident_response_structure_details.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/incident_response_structure_SRE_pyramid.png"
     alt="incident_response_structure_SRE_pyramid.png"
     style="float: left; margin-right: 10px;" />

#### List of SRE processes

<img src="../images/list_processes.png"
     alt="list_processes.png"
     style="float: left; margin-right: 10px;" />


#### 12-factor guidelines on administration and management tasks 

<img src="../images/incident_response_12-factor_Admin_Mgmt_guidelines.png"
     alt="incident_response_12-factor_Admin_Mgmt_guidelines.png"
     style="float: left; margin-right: 10px;" />

#### Build a playbook based on alerts

<img src="../images/incident_response_alerts_and_processes.png"
     alt="incident_response_alerts_and_processes.png"
     style="float: left; margin-right: 10px;" />

##### Create "easy buttons" for quick fix

<img src="../images/incident_response_use_microservices_and_APIs.png"
     alt="incident_response_use_microservices_and_APIs.png"
     style="float: left; margin-right: 10px;" />

##### Balance interrupt-driven work and Incident Response

Controlled burns vs Fire fighters again.

<img src="../images/incident_response_balance_project_driven_incident_response.png"
     alt="incident_response_balance_project_driven_incident_response.png"
     style="float: left; margin-right: 10px;" />

This module covered deploying, operating, and maintaining your design. Much of the groundwork needed for successful deployment monitoring and incident response was established earlier in the course in the context of the design process. This module points out how to integrate all those elements together to promote the behaviors that will lead to a stable service.

### Application: Stabilization & Operation

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/0c9fQ/stabilization-and-operation)

The photo service has evolved into a sophisticated scalable, reliable, secure system.

The goal is to **stabilize the system** and **make it maintainable** and **operable**.

* What elements of the service should be monitored?
* What kinds of alerts and notifications would you set up?

<img src="../images/application_photo_Service_stabilization_operation.png"
     alt="application_photo_Service_stabilization_operation.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/application_photo_Service_current_architecture.png"
     alt="application_photo_Service_current_architecture.png"
     style="float: left; margin-right: 10px;" />
     
<img src="../images/application_photo_Service_what_to_monitor.png"
     alt="application_photo_Service_what_to_monitor.png"
     style="float: left; margin-right: 10px;" />


### Design Challenge #7: Monitoring & Alerting

[video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/9SKko/design-challenge-7-monitoring-and-alerting)


Monitoring & Alerting are **what you add to the log system to stabilize a solution**.


<img src="../images/application_photo_Service_logging_current_architecture.png"
     alt="application_photo_Service_logging_current_architecture.png"
     style="float: left; margin-right: 10px;" />

#### Business Challenge

What you think might be important to monitor, and under what conditions alerts and notifications should be sent?

<img src="../images/application_photo_Service_logging_business_challenge.png"
     alt="application_photo_Service_logging_business_challenge.png"
     style="float: left; margin-right: 10px;" />

So in this case, make a list of three monitoring and alerting items that you would put into place to support stabilizing this particular solution. 

#### What monitoring and alerting to set up for the logs
     
<img src="../images/application_photo_Service_logging_solution_logs_watchdogs.png"
     alt="application_photo_Service_logging_solution_logs_watchdogs.png"
     style="float: left; margin-right: 10px;" />

- monitor that latest data in BigTable isn't older than few minutes > **white box**
- monitor the queue mechanisms in Pub/Sub for all 3 feeds (web, app, data) > **black box**
- monitor network latency, network uptime for all 3 feeds > **black box**

#### Google's reference architectures online

<img src="../images/application_photo_Service_logging_solution_logs_Google_tutorials.png"
     alt="application_photo_Service_logging_solution_logs_Google_tutorials.png"
     style="float: left; margin-right: 10px;" />


### Lab: Deployment Manager - Full Production

- [video](https://www.coursera.org/learn/cloud-infrastructure-design-process/lecture/UERcn/deployment-manager-full-production)
- [lab notes](../labs/lab_Deployment_Manager_Full_Production.md)

In this final lab, you'll clone a public repository of deployment manager templates. The public repo is a library of templates that are provided for a variety of purposes.

They provide a flexible base of templates that you can build on to create your own deployment solutions. There are several tutorials available in the online documentation that use the templates in the repo. This lab is based on one of the advanced tutorials. It employs many of the **best practices** and **design principles** you've learned in this class. It creates a scalable, resilient full production service **around a simple logbook application**.

The lab goes beyond the tutorial, by adding monitoring and testing. You'll use stac driver to configure monitoring, alert notifications and to set up graphical dashboards.

- You'll use [Apache Bench](https://httpd.apache.org/docs/2.4/programs/ab.html) to generate load traffic to test the system and trigger auto scaling. 
- You'll also simulate a service outage to test notifications and resiliency features.

During the previous labs in this course you learned a lot about the basic use of deployment manager. In this final lab, you'll clone a public repo of example Deployment Manager templates that you can use as reference for developing advanced deployments. The previous labs all used YAML templates and Jinja2 templates. This final lab uses Python templates. You'll deploy a full production application that implements many of the principles that were discussed and applied during the class.

<img src="../images/lab_full_production.png"
     alt="lab_full_production.png"
     style="float: left; margin-right: 10px;" />

<img src="../images/lab_full_production_architecture.png"
     alt="lab_full_production_architecture.png"
     style="float: left; margin-right: 10px;" />



## Resources/Articles

- [**Perfkit Benchmarker**](https://github.com/GoogleCloudPlatform/PerfKitBenchmarker): PerfKit Benchmarker is an open effort to define a canonical set of benchmarks to measure and compare cloud offerings.
- **Price calculator**: [cloud.google.com/products/calculator/](https://cloud.google.com/products/calculator/)
- Google's **Site Reliability Engineering**: https://landing.google.com/sre/books/
- Google's **The Site Reliability Workbook**: https://landing.google.com/sre/books/
- [**GCP podcast about Pokémon GO**](https://www.gcppodcast.com/post/episode-57-pokemon-go-with-edward-wu/) with Edward Wu, Director of Software Engineering at Niantic
- GCP solutions: https://cloud.google.com/solutions
- **GCP tutorials & solutions**: https://cloud.google.com/docs/tutorials
- [Apache Bench](https://httpd.apache.org/docs/2.4/programs/ab.html) to generate load traffic to test the system and trigger auto scaling. 
-  Step-by-step tutorials: https://cloud.google.com/deployment-manager/docs/tutorials
