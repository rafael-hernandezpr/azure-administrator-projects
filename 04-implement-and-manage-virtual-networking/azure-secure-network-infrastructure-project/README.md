# Azure Secure Network Infrastructure Project

## Project Overview

This project demonstrates the design, implementation, security, and troubleshooting of a multi-tier Azure network environment.

The environment was built to simulate a small enterprise-style multi-tier network architecture with separate web and backend network tiers, controlled connectivity between virtual networks, secure access to Azure Storage, private name resolution, traffic distribution through Azure Load Balancer, and network troubleshooting using Azure Network Watcher.

The project focuses on applying Azure networking concepts in a practical environment rather than configuring isolated services individually.

## Business Scenario

A company is hosting a web-based application in Azure and needs a network design that separates public-facing web servers from backend systems while maintaining secure communication between both tiers.

The environment must:

- Allow users to access the web application through a single public endpoint.
- Distribute incoming traffic across multiple web servers for availability.
- Keep backend systems isolated from direct internet exposure.
- Control communication between the web and backend tiers.
- Provide secure access to Azure Storage.
- Support private access to Azure PaaS services using Private Endpoint and Private DNS.
- Allow administrators to troubleshoot connectivity, routing, security rules, and service availability when failures occur.

This project implements a secure multi-tier Azure network architecture that addresses those requirements.

## Project Highlights

- Designed a segmented Azure network using separate web and backend virtual networks.
- Connected application tiers privately using Azure VNet peering.
- Secured subnet traffic using Network Security Groups and Application Security Groups.
- Implemented User Defined Route testing to validate routing behavior and troubleshoot connectivity failures.
- Configured Azure Storage access using both Service Endpoint and Private Endpoint architectures.
- Implemented Azure Private DNS so storage traffic resolved to the private endpoint IP address.
- Deployed a Standard Azure Load Balancer across two IIS web servers.
- Validated backend health and failover by intentionally stopping one web service.
- Used Azure Network Watcher to troubleshoot NSG, routing, and application-port connectivity problems.

## Architecture

The environment uses two separate Azure virtual networks to isolate the web and backend tiers while allowing controlled private communication between them.

- **vnet-web (10.10.0.0/16)**
  - WebSubnet (10.10.1.0/24)
  - WebVM01
  - WebVM02
  - NSG-Web
  - ASG-Web
  - Route table for UDR testing

- **vnet-backend (10.20.0.0/16)**
  - BackendSubnet (10.20.1.0/24)
  - BackendVM01
  - NSG-Backend
  - PrivateEndpointSubnet (10.20.2.0/24)
  - Azure Storage Private Endpoint

The two VNets are connected using VNet peering. Azure Load Balancer provides a single public entry point for the web tier, while Azure Storage is accessed securely using Service Endpoint and Private Endpoint configurations with Private DNS.

## Azure Resources and Services Used

- Azure Virtual Networks, Subnets, and VNet Peering
- Network Security Groups (NSGs) and Application Security Groups (ASGs)
- Route Tables and User Defined Routes (UDRs)
- Azure Virtual Machines and Azure Load Balancer
- Health Probes and Load Balancing Rules
- Azure Storage Account with Service Endpoints and Private Endpoints
- Azure Private DNS Zones
- Azure Network Watcher with Connection Troubleshoot, NSG Diagnostics, and Next Hop

## Implementation Steps

1. Created separate web and backend virtual networks with dedicated subnets.
2. Connected both VNets using VNet peering and validated private connectivity.
3. Secured traffic using NSGs and an Application Security Group for the web tier.
4. Configured route table and UDR testing to validate routing behavior.
5. Secured Azure Storage using Service Endpoint, Private Endpoint, and Private DNS.
6. Deployed Azure Load Balancer across WebVM01 and WebVM02 with a health probe.
7. Validated load balancing, backend failover, and service recovery.
8. Used Azure Network Watcher to troubleshoot NSG, routing, and port connectivity issues.

9. ## Validation and Troubleshooting Results

- Confirmed private connectivity between the web and backend tiers through VNet peering.
- Verified Azure Storage private name resolution to the Private Endpoint IP.
- Confirmed load distribution between WebVM01 and WebVM02 through Azure Load Balancer.
- Simulated a web server failure and verified traffic continued through the healthy backend.
- Diagnosed a UDR routing failure using Network Watcher and Next Hop.
- Diagnosed an NSG deny rule using NSG Diagnostics.
- Identified an application-port failure when BackendVM01 was not listening on TCP 8080.

