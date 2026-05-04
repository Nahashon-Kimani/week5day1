# Database HA Lab

This repository contains a comprehensive guide and implementation for setting up a highly available database infrastructure on AWS.

## Contents

### Documentation Files

- **[Amazon RDS HA.md](./Amazon%20RDS%20HA.md)** - Detailed guide on setting up Amazon RDS with high availability configuration, including multi-AZ deployments and failover strategies.

- **[hosting.md](./hosting.md)** - Instructions for hosting the application and configuring the necessary infrastructure components.

- **[cleanup.md](./cleanup.md)** - Step-by-step procedures for cleaning up and deprovisioning resources to avoid unnecessary AWS charges.

### Application Files

- **[index.php](./index.php)** - Main application file containing the PHP backend logic for interacting with the RDS database.

## Overview

This lab demonstrates best practices for implementing a highly available database architecture on Amazon Web Services (AWS), including:

- Multi-AZ RDS deployment for automatic failover
- Database connectivity and management
- Application configuration for resilience
- Resource cleanup procedures

## Getting Started

1. Review the [Amazon RDS HA.md](./Amazon%20RDS%20HA.md) documentation to understand the infrastructure setup
2. Follow the [hosting.md](./hosting.md) guide to deploy the application
3. Use [index.php](./index.php) as your application entry point
4. Refer to [cleanup.md](./cleanup.md) when you need to tear down resources

## Prerequisites

- AWS Account with appropriate permissions
- PHP environment
- MySQL/MariaDB knowledge
- Basic understanding of AWS RDS and high availability concepts
