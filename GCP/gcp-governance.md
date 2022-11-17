# GCP Governance Guidelines 

## Project Creation
All new projects must be approved by department managers and include an estimated monthly budget.  

### **Naming Convention**
Projects must follow the COMPANY GCP naming convention.  

**Requirements:**   
●	No longer than 32 characters   
●	The Project name must match the project ID (personal preference)  
●	All lowercase project ID  


**Format:**  
```
(company)-(dept)-(business unit/app)-(environment)
```

**Environments:**  
●	prod	- Production   
●	poc	    - Proof-of-concept or demo  
●	test	- Dev, test, or QA  
●	stage   - Staging environment  

_Examples:_  
```
company-eng-innovations-prod  
company-sales-mobileapp-stage  
company-marketing-website-dev  
```
  

## Folder Selection
Each project must be assigned to a department folder. Please ask the requestor for the department the project belongs to.

The following is the approved GCP Resource Hierarchy:
![GCP Hierarchy Example](/img/gcp-hierarchy.png)

## Tagging
Each project must be tagged with the following key/value pairs:  
●	dept - This should be the same as the folder the project is under  
●	dept-owner - The department manager’s username (first.last)  
●	project-owner - The individual’s username that is responsible for the project. Usually the requestor.  
●	Environment - Environment of project or resource  
●	TFState  - (true/false) Deployed via Terraform and will maintain a managed state file  

## Resource Creation 
### **Naming Convention (optional)**
* 64 character limit  
```
(company)-(dept)-(business unit/app)-(environment)-(resource)
```
_Examples_  
```
company-eng-innovations-prod-sqldb  
company-sales-mobileapp-stage-vm1  
company-marketing-website-dev-vpc
```
## General Guidelines
### **Principle of Least Privilege**
Least privilege access controls restrict access rights for users, accounts, and processes to only those resources absolutely required to perform routine, legitimate activities.   
For all projects, ensure you are following the principle of least privilege. Only grant users the access they need to complete their work.  

**Connectivity to Other Projects or COMPANY Corporate Networks**  
No VPCs should be peered to the <PRIMARY SHARED VPC> VPC or any other VPC without prior approval from COMPANY’s CloudOps team.

**Use Identity Aware Proxy**  
Utilize Identity Aware Proxy (IAP) instead of opening SSH or RDP to the internet. This allows tunneling of TCP connections in a more secure manner than opening SSH or RDP to the internet. More information can be found here.

**No External IP Addresses Directly Attached to VM Instances**  
All outbound traffic should use Cloud NAT and any service that requires inbound traffic for more than testing purposes should use a load balancer. There are a few exceptions to this due to legacy applications.

**IAM Policy**  
Only grant access to Google Cloud resources by granting access to COMPANY members. Members can be one of the following types:

●	Google Groups (for GCP Console access)  
●	Service Account (Use service account only for machine to machine connectivity)  
●	Individual Google Accounts should be highly discouraged as much as possible  
●	Only assign access to COMPANY.com accounts, no contractor or outside email accounts. If a contractor needs an account they can reach out to the IT department  

