#  Enterprise RBAC & Identity Lifecycle Project | Microsoft Azure

## Project Overview

This project role-plays an existing small-business Azure environment in which the company, employees, Microsoft Entra identities, Azure subscription structure, resource groups, and supporting test resources are treated as already established.

To make the simulation possible, the required users, security groups, resource groups, and Azure resources were preconfigured as lab prerequisites. These setup activities are not the primary focus of the project.

The project instead focuses on the day-to-day responsibilities of an Azure Administrator operating within an active business environment. The goal was to simulate realistic identity, access, and governance operations rather than simply demonstrate how to create Azure resources.

Throughout the project, I responded to business requests, access changes, security incidents, and employee lifecycle events while applying least-privilege principles and validating the resulting permissions directly in Azure.

## Project Highlights

- Implemented scoped Azure RBAC across subscription and resource-group levels using Owner, Contributor, Network Contributor, and Reader roles.
- Configured delegated administration with Azure RBAC conditions to restrict which roles managers could assign and to whom.
- Used Microsoft Entra security groups for scalable group-based access and validated effective permissions through inheritance and membership.
- Configured and tested Self-Service Password Reset (SSPR) using registered authentication methods.
- Simulated employee onboarding, department transfer, offboarding, soft-delete recovery, and rehire scenarios.
- Investigated excessive privileges, hidden access paths, and administrative changes using IAM views and Azure Activity Log.

## Business Scenario

The organization is a small business already operating in Microsoft Azure. Its Microsoft Entra tenant, employee identities, Azure subscription, departmental resource groups, and supporting test resources are treated as part of an existing environment.

The company operates multiple departments, including IT Production, Networking, and Development. Managers are responsible for their departments, employees require different levels of Azure access, and an auditor independently reviews permissions and administrative activity.

As the Azure Administrator, I am responsible for maintaining secure access across the environment while responding to day-to-day operational events such as access requests, delegated administration, employee onboarding, department transfers, password recovery, excessive privilege incidents, offboarding, account restoration, and access reviews.

The objective is to support normal business operations while maintaining least privilege, separation of duties, controlled delegation, and auditable access management.

## Environment / Roles

| Identity | Business Role | Azure / Entra Responsibility |
|---|---|---|
| Rafael | Azure Administrator / Director | Subscription Owner and final authority for access and governance |
| Cloud Admin | Entra Administrator | Microsoft Entra identity and authentication administration |
| Sarah | IT Manager | Manages access to the IT Production environment |
| Alex | IT Employee | Contributor access to IT Production resources |
| Michael | Networking Manager | Manages access to the Networking environment |
| Emily | Network Technician | Network Contributor within the Networking resource group |
| Chris | Employee / Department Transfer | Initially onboarded to Development and later transferred to Networking |
| David | Developer | Receives Development access through Microsoft Entra security-group membership |
| John | Auditor | Subscription Reader responsible for reviewing access and administrative activity |

## Implementation / Role-Play Scenarios

### 1. Delegated RBAC Administration
Department managers were granted scoped Owner access with RBAC conditions that limited which roles they could assign and to which employees.

- Sarah managed IT Production access and could delegate Contributor only to Alex.
- Michael managed Networking access and could delegate Network Contributor only to approved employees.
- This demonstrated controlled delegation without giving managers unrestricted RBAC authority.

### 2. Group-Based Development Access
Development access was managed through the `GRP-Azure-Developers` Microsoft Entra security group.

- The group received Contributor access to `RG-Development`.
- Developers inherited access through group membership instead of direct role assignment.
- Effective access was validated using Azure IAM Check access.

### 3. Self-Service Password Reset
SSPR was enabled for a selected Microsoft Entra security group.

- Alex was added to the SSPR-enabled group.
- SMS was configured as an authentication method.
- A forgotten-password scenario was simulated.
- Alex successfully reset the password and regained Azure portal access.

### 4. Employee Onboarding and Department Transfer
Chris was onboarded as a new employee and initially received Development access through group membership.

Later, Chris transferred to Networking:

- Development access was removed.
- Michael's delegated RBAC condition was updated to allow access assignment to Chris.
- Chris received Network Contributor access to `RG-Networking`.

### 5. Excessive Privilege Incident
Emily was intentionally granted Owner at the subscription scope to simulate a privilege misconfiguration.

- The excessive role allowed access outside the Networking department.
- An unauthorized resource group was created to demonstrate the blast radius.
- John identified the excessive permission during an audit.
- Azure Activity Log was used to trace the role assignment.
- The Owner assignment was removed and least privilege was restored.

### 6. Hidden Access Troubleshooting
David had both direct Contributor access and group-based Contributor access to Development.

- The direct role assignment was removed.
- David still retained access.
- IAM Check access revealed that the remaining permission came from `GRP-Azure-Developers`.
- Removing David from the group eliminated the effective access.

### 7. Offboarding and Account Recovery
David was offboarded through a full identity lifecycle process:

- Group and RBAC access removed
- Account disabled
- Active sessions revoked
- User deleted

The account was then restored from Microsoft Entra soft deletion during a simulated rehire scenario.

### 8. Final Audit and Governance Review
John performed a subscription and resource-group access audit.

The final review verified:

- Correct subscription-level Owner and Reader assignments
- Scoped departmental permissions
- Group-based Development access
- Inherited access behavior
- Removal of excessive privileges
- Controlled manager delegation

## Validation / Evidence

The project was validated throughout the role-play using Azure Portal screenshots and IAM verification.

Key evidence included:

- Scoped RBAC assignments for IT Production, Networking, and Development
- RBAC conditions restricting delegated role assignment
- Group-based Contributor access through `GRP-Azure-Developers`
- Successful Self-Service Password Reset and restored sign-in
- Employee transfer from Development to Networking
- Excessive subscription-level Owner access detection and remediation
- Azure Activity Log evidence showing role assignment activity
- Hidden access troubleshooting through effective-permission checks
- Employee offboarding, session revocation, soft deletion, and recovery
- Final subscription and resource-group access audits
