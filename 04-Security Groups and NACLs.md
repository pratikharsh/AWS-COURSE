# AWS Security: Security Groups and NACLs 🔐

## Security Groups: 🛡️
- **Function:** Virtual firewalls for EC2 instances.
- **Rules:** Control inbound and outbound traffic via protocols, ports, and IPs.
- **Association:** One or more security groups per EC2 instance.
- **Inbound Rules:** Allow traffic to the instance.
- **Outbound Rules:** Control traffic leaving the instance.
- **Configuration:** Use IP addresses, CIDR blocks, security group IDs, or DNS names.
- **Operation:** Evaluate rules before allowing traffic.
- **Statefulness:** Automatically allows corresponding outbound traffic if inbound is allowed, and vice versa.
- **Changes:** Immediate effect.

## Network Access Control Lists (NACLs): 🔒
- **Function:** Stateless traffic filters at the subnet level.
- **Association:** One NACL per subnet; multiple subnets can share the same NACL.
- **Rules:** Numbered list evaluated in ascending order.
- **Rule Components:** Rule number, protocol, action (allow/deny), IP range, port range, ICMP type.
- **Configuration:** Allow or deny specific traffic types.
- **Statefulness:** Stateless; must explicitly allow corresponding outbound traffic.
- **Changes:** May take time to propagate.

## Key Differences: ⚖️
- **Level:** Security Groups operate at the instance level; NACLs at the subnet level.
- **Statefulness:** Security Groups are stateful; NACLs are stateless.
- **Rule Propagation:** Security Group changes are immediate; NACL changes may take time.
![image](https://github.com/user-attachments/assets/50291ecf-b09e-4a51-960d-e42ffe066a55)
