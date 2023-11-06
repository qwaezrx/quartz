

Offers variety of services such as:
- [[VM|virtual machines]]
- [[GKE|Google Kubernetes Engine]]
- Compute Engine
- App Engine
- Cloud Functions
- Cloud Run


## Services on Google Cloud
### Compute Engine
 - [[IaaS]] offering
	- Compute
	- Storage
	- Network
- Predefined and customized [[VM]]s
- Persistent disks and local [[SSD]]s
- Managed instance groups
- Per-second billing

Popular because:
- (+) Provides complete control over infrastructure since [[OS|operating system]]s can be customized, and it can run apps that rely on a mix of operating systems.
- (+) [[On-premise]]s workloads can easily be lifted and shifted to Google Cloud without needing to rewrite.
- (+) It's best option when other computing options don't support your application or requirements.


### Google Kubernetes Engine
- [[GKE|Google Kubernetes Engine]] runs containerized applications in a Cloud environment
- Code packaged with all of its dependencies

### App Engine
- is a fully managed [[PaaS]] offering
- Bind code to libraries
- Focused on app logic
- Deploys required infrastructure (different languages)
- Integrated with Cloud tools
- Version control + traffic splitting

- (+) can focus on writing code
- (+) can focus on building apps instead of deploying and managing the environment

#### Common examples using App Engine
- Websites
- Mobile app and gaming back-end
- RESTful API

### Cloud Functions
- Event-based, asynchronous compute solution
- Executes code in response to events
- Functions as a service offering
- Deploys the computing capacity to run code
- Can connect and extend cloud services
- Bills to the nearest 100 milliseconds

#### Common Cloud Functions
- It can be part of a [[Microservice]]s application architecture
- It is used to build simple, serverless mobile or IoT backends or integrate with third-party services and APIs
- It can be part of AI services such as:
	- virtual assistant
	- video or image analysis
	- sentiment analysis

### Cloud Run
- A managed compute platform
- Runs stateless containers
- Serverless
- Built on Knative
- Fast

### Cloud Build

![[Pasted image 20231019233611.png]]

Service for building [[Container|containers]].

- Integrated with Cloud IAM
- Designed to retrieve the source code builds from different code repositories such as:
	- Cloud Source Repositories
	- GitHub
	- Bitbucket
- Each build step in Cloud Build runs in a Docker container
- Google Build can deliver newly built images to various execution environments such as:
	- [[GKE|Google Kubernetes Engine]]
	- App Engine
	- Cloud Function

## Resources behind Google Cloud

#### Physical Assets
- Servers

#### Virtual Resources
- [[VM|virtual machines]]
- [[Container|containers]]

### Network
Google's network carries as much as 40% of the world's Internet traffic every day. (2022)
- Highest possible throughput
- Lowest possible latencies
- 100+ content caching nodes worldwide
- High demand content is cached for quicker access

#### Network Service Locations
Infrastructure based in five major geographic locations:
- North America
- South America
- Europe
- Asia
- Australia

## Resource Management
Every Google resource you use must belong to a project.

>[!project]
>A project is a container for all your Google Cloud resources such as:
>- organize resources
>- mange billing
>- control access
>Each project has unique identifier

### Resource Hierarchy

![[Google_Cloud_hierarchy.png]]

The resource hierarchy directly relates to how policies are managed and applied on Google Cloud.

#### Level 1: Resources
Each resources belongs to exactly one project.

#### Level 2: Projects
Projects are the basis for enabling and using Google Cloud Services like:
- managing APIs
- enabling billing
- removing collaborators
- etc.

__Project Identifiers__:
- Project ID
	- Globally unique
	- Assigned by Google Cloud
	- Immutable
- Project name
	- Not unique
	- Chosen by user
	- Mutable
- Project number
	- Same as Project ID

#### Level 3: Folders
Use folders to group projects under an organization in a __hierarchy__

![[Google_Cloud_Folders.png]]

- Folders give teams the ability to delegate administrative rights so they can work independently.
- Can limit access to different folders with Identity and Access Management (IAM)

>[!IAM]
>with IAM, administrators can apply policies that define who can do what and done with on which resources.

#### Shared Responsibility
If you configure or store it, you're responsible for securing it.

##### Cloud Provider
- Hardware
- Networks
- Physical security
##### Customer
- Configurations
- Access policies
- User data

No matter which cloud provider you use, there is a __shared responsibility__.


## Billing
- Billing is established at the project level
- A billing account can be linked to zero or more projects
- Billing accounts are charged automatically and invoiced every month, or at every threshold limit.
- Billing subaccounts can be used to separate billing by project.

###### How to prevent accidentally running up a big Google Cloud bill?
- Budgets
- Alerts
- Reports
- Quotas
	- Rate quota: Resets after a specific time
	- Allocation quota: Governs number of resources
	- You can change some quotas by requesting an increase from Google Support.

## Interacting with Google Cloud
### Google Cloud Console
- Simple web-based GUI
- have full management control over:
	- Easily find resources, 
	- check their health, 
	- set budgets
- search facility to find resources and connect to instances through [[SSH]] in the browser.
### Cloud SDK and Cloud Shell
#### Cloud SDK
- Set of tools to manage resource and apps hosted on Google Cloud
	- __gcloud tool__: provides the main command-line interface for Google Cloud products and services
	- __gsutil__: provides access to Cloud Storage from the command line
	- __bq__: A command-line tool for BigQuery
#### Cloud Shell
- Provides command-line access to cloud services directly from a browser
- Debian-based virtual machine with a persistent 5-GB home directory
- Each Cloud shell VM is [[ephemeral]]
- Provides web preview functionality and built-in auth for access to Cloud console projects and resources, including your [[GKE]] resources

- The Cloud SDK gcloud command and other utilities are always installed, available, up to date, and fully authenticated

### APIs
- The services that make up Google Cloud offer [[API]]s so that code you write can control them
- Google APIs Explorer: shows available APIs, and in which versions
- Can use APIs to build apps that allocate and manage Google Cloud resources

### Google Cloud App
- Start, stop, and use [[SSH]] to connect to Compute Engine instances and see logs from each instances.
- Stop, start Google SQL instances
- Administer apps deployed on App Engine by:
	- viewing errors
	- rolling back deployments
	- changing traffic splitting

