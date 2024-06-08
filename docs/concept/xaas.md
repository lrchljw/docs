---
title: IaaS, IaC, PaaS, SaaS, FaaS, XaaS
---

## IaaS

- Infrastructure as a Service (IaaS) is a **cloud computing service model**.
- It allows accessing and managing resources **without the need to purchase and maintain physical hardware**.
- Instead it provides **virtualized computing resources** such as servers, storage, and networking.

### Features and Benefits

**Virtualized Resources**

VMs, storage, and networking resources.

**On-Demand Usage**

Adjust resource and pay only for the resources being used, **control costs** effectively.

**Automated Management**

Management and monitoring **automation tools**, such as load balancing, backup, and recovery.

**High Availability and Scalability**

Data centers in **multiple geographic locations** ensuring disaster recovery capabilities.

**Security and Compliance**

Data encryption, access control, and compliance certifications.

**Use Cases**

- Development and testing environments.
- Data storage and backup.
- High-performance computing.
- Web application hosting.

## IaC

- Infrastructure as Code (IaC)
- Managing computing infrastructure through configuration files.
- Rather than through physical hardware configuration or interactive configuration tools.

**Benefits:**

- Efficiency: Reduces time and errors associated with manual setup.
- Consistency: Ensures all environments are set up the same way, avoiding drift.
- Auditability: Changes are tracked (config files in GIT) and can be reviewed, making the infrastructure more secure and manageable.

**Example Tools:**

- Terraform: An open-source tool that works with many cloud providers (AWS, Azure, Google Cloud) to manage resources.
- AWS CloudFormation: A service from Amazon to manage AWS resources.
- Ansible: An open-source tool that uses simple YAML files to manage configurations and deployments.

**Example:**

Using Terraform to create a web server on AWS:

```hcl
provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "example-instance"
  }
}
```

Running `terraform apply` would create an EC2 instance with the specified configuration.
