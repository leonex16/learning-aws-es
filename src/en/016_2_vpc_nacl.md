# Network Access Control List ( NACLs )

An ( optional ) layer of security that acts as as
<span class="text-red">**firewall**</span>
for controlling traffic **in and out of**
<span class="text-red">**subnet(s)**</span>

## Introduction

### Use Case

We determine there is a malicious actor at a specific
IP address is trying to access our instances so we block
their IP

We never eed to SSH into instances so we add a DENY for
these subnets. This is just an additional measure in
case our Security Groups SSH port was left open

<img
  src="../../public/images/vpc/nacl.png"
  alt="NACLs" />

## Cheat Sheet

- Network Access Control List is commonly known as NACLs
- VPCs are automatically given a default NACLs which allows
**all** outbound and inbound traffic
- Each subnet within a VPC must bu associated with a NACLs
- Subnets can only be associated with 1 NACLs at a time.
Associating a subnet with a new NACs will remove the
previous association
- If a NACLs is not explicitly associated with a subnet,
the subnet will automatically be associated with the
default NACLs
- NACLs has inbound and outbound rules. Just like Security Groups
- Rule can either **allow** or **deny** traffic.
Unlike Security Groups which can only allow
- NACLs are STATELESS ( any allowed inbound traffic is also
allowed outbound )
- When you create a NACLs it will deny all traffic by default
- NACLs contain a numbered lits of rules that gets evaluated
in orden from lowest to highest
- If you needed to block a single IP address you could via NACLs
  
<style>
.text-red {
  color: red;
}
</style>
