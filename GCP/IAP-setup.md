Setup IAP Access

Create Firewall Rule
  Name: allow-ingress-from-iap
  Direction of traffic: Ingress
  Target: All instances in the network
  Source filter: IP ranges
  Source IP ranges: 35.235.240.0/20
  Protocols and ports: Select TCP and enter 22,3389 to allow both RDP and SSH.

Grant the following access
  - In the main IAM page, https://console.cloud.google.com/iam-admin/iam?project=your_project grant the user the "Compute Viewer" and "Service Account User" roles.
  - In the VMs page, https://console.cloud.google.com/compute/instances?folder=&organizationId=&project=your_project, select one or more VM´s and grant the user the "Compute Instance Admin (v1)" role.
  - On the IAP page, https://console.cloud.google.com/security/iap?project=your_project, select the VM and give the user the "IAP-secured Tunnel User" role
