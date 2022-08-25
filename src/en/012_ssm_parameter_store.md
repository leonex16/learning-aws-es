# SSM Parameter Store

**Secure**, **hierarchical storage** for configuration
data management and secrets management

## Introduction

You can store data such as passwords, database strings, and
license codes as parameter values

Store configuration data and secure strings in
**hierarchies** and **track versions**

You can encrypt parameters using KMS

You group parameters together based on the naming convention
**by using forwards slashes**. This is how you create
**hierarchies**. This allows you to fetch all parameters at
different levels. Eg. /exampro/application/prod

You choose a tier which limits how many parameters and
the size of the values

Type can be:

- **String** - Just a string
- **StringList** - Comma separate string
- **SecureString** - Encrypted string with KMS

## Parameter Tiers

|                         | **Standard** | **Advanced**              |
|-------------------------|--------------|---------------------------|
| Number of params        | 10.000       | 100.000                   |
| Max size of param value | 4KB          | 8KB                       |
| Parameter Policies      | No           | Yes                       |
| Cost                    | Free         | $0.05 per parameter/month |

You can change standard parameter to an advanced parameter
at any time, but
<span class="text-red">**you can't revert advanced
parameter to a standard parameter**</span>

Reverting an advanced parameter to a standard parameter
**would result in data loss** because the system would
truncate the size of the parameter from 8KB to 4KB

## Parameter Policies

Parameter policies are helpful in
**forcing you to update or delete passwords**

Using asynchronous, periodic scans. After you create a policy,
**you don't need to perform additional actions to enforce
the policy**

You **can assign multiple** policies to a parameter

There are 3 types of policies:

- **Expiration**
  - This <span class="text-red">**policy deletes the parameter**</span>
  after a specified date an time
- **ExpirationNotification**
  - This policy triggers an event in Amazon CloudWatch events
  that <span class="text-red">**notifies you about the
  upcoming expiration**</span>
- **NoChangeNotification**
  - This policy triggers an event in Amazon CloudWatch
  <span class="text-red">**if a parameter has not been
  modified for a specified period of time**</span>.
  This policy type is useful when, for example, a password
  needs to be changed within a period of time

## CLI Hierarchy Examples

```bash
aws ssm put-parameter --name "/planets/vulcan/population"     --value "4.9B" --type String
aws ssm put-parameter --name "/planets/vulcan/gravity"        --value "1.4G" --type String
aws ssm put-parameter --name "/planets/vulcan/classification" --value "M"    --type String
```

```bash
aws ssm get-parameters-by-path --path "/planets/vulcan"
```

<style>
.text-red {
  color: red;
}
</style>
