# Secrets Manager

**Protect secrets** needed to access your applications and
services. Easily rotate, manage and retrieve database credentials,
API keys, and other secrets throughout their lifecycle

## Introduction

Secrets Manager's is mostly used to store and automatically
rotate database credentials

There are 5 secrets types available:

- Credentials for RDS databases
- Credentials for Redshift cluster
- Credentials for DocumentDB databases
- Credentials for other database
- Other type of secrets

**Enforces** encryption at-rest by using KMS

**CloudTrail** can monitor credentials access in
case you need to audit

### Pricing

- $0.40 per secret per month
- $0.05 per 10.000 API calls

<style>
.text-red {
  color: red;
}
</style>
