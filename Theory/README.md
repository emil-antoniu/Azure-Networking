# General Troubleshooting

The first step in troubleshooting a network‑related problem is **identifying the scope**:

- If **one user** is affected → likely a configuration issue on that user's device.
- If **all users** are affected → likely a server or network infrastructure issue.
- If **a group of users** is affected → determine what their devices have in common.

---

## A Logical Troubleshooting Approach

### Can you duplicate the issue?
Helps confirm whether the issue is real or caused by user error.

### What is working?
Determines the nature of the issue.  
Example: A server can reach local resources but not remote ones.

### What is not working?
Further clarifies the problem.  
Example: A server cannot connect to a remote resource but can resolve its DNS name.

### How are the working and non‑working elements related?
Examples:
- Connecting to local resources → IP stack is functioning.
- Resolving remote addresses → DNS is functioning.
- If DNS is on another network → default gateway is functioning.

### Does it work for other systems?
If another system also fails to access the same resource, the issue likely lies with:
- The infrastructure  
- The remote resource itself

### Has it worked in the past?
If the resource is new, it may simply not be ready yet.

### What has changed since it last worked?
Consider:
- New networking components installed?
- IP addressing scheme changed?