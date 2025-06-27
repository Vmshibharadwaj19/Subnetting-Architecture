
# AWS VPC and Subnetting Project

This project demonstrates how to create a custom Virtual Private Cloud (VPC) in AWS with public and private subnets distributed across multiple Availability Zones.

## 🧠 Architecture Overview

![VPC Architecture Diagram](docs/images/vpc-subnet-architecture.png)

## 📦 AWS Services Used

- **Amazon VPC** – Network isolation
- **Subnets** – Public and Private segments
- **Internet Gateway (IGW)** – Access to internet for public subnets
- **NAT Gateway** – Internet access for private subnets
- **Route Tables** – Control traffic routing
- **EC2** – Instances placed in different subnets
- **Security Groups & NACLs** – Traffic filtering

## 📐 Subnetting Strategy

| Subnet Type | CIDR Block        | Availability Zone | Description             |
|-------------|-------------------|--------------------|--------------------------|
| Public A    | 10.0.1.0/24       | us-east-1a         | Hosts web servers       |
| Public B    | 10.0.2.0/24       | us-east-1b         | For HA configuration    |
| Private A   | 10.0.3.0/24       | us-east-1a         | Hosts app servers       |
| Private B   | 10.0.4.0/24       | us-east-1b         | Hosts DB instances      |

## 🚀 Deployment Steps

1. Create a custom VPC with CIDR block `10.0.0.0/16`
2. Create 4 subnets using above strategy
3. Attach an Internet Gateway to the VPC
4. Create a NAT Gateway in a public subnet
5. Create route tables:
   - Public Route Table: routes `0.0.0.0/0` to IGW
   - Private Route Table: routes `0.0.0.0/0` to NAT
6. Launch EC2 instances in each subnet to test connectivity

## 📸 Proof of Deployment

- `docs/images/vpc-console.png` – VPC Overview
- `docs/images/subnets.png` – Subnet list
- `docs/images/route-tables.png` – Route Tables
- `docs/images/instances.png` – Deployed EC2 Instances

## 📚 Resources

- [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/)
- [Subnetting in AWS Guide](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html)
- [AWS CIDR Calculator](https://cidr.xyz/)
