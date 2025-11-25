# IP Subnetting (Beginner-Friendly Notes)

Subnetting is the skill of taking a big network and breaking it into
smaller networks so devices know who is “local” and who is “somewhere else.”

If IP addresses are like home addresses, then subnetting defines the 
neighborhoods.

---

## 1. What Is an IP Address?

An IP address has **4 numbers**, called *octets*, separated by dots:

Example:
192.168.10.25

Each of those numbers goes from **0 to 255**.

That’s because each octet is made from **8 bits**, and 8 bits can represent
256 different values (0 through 255).

8 bits → 2^8 = 256 total values


---

## 2. What Is a Subnet?

A subnet is just a smaller piece of a bigger network.

Why break a network into subnets?
- It keeps traffic organized  
- It improves performance  
- It controls access  
- It tells devices who is “local”  
- It tells routers when to forward traffic elsewhere  

---

## 3. What Is a Subnet Mask?

A subnet mask tells you **which part of an IP address is the network portion**
and **which part is the host portion**.

Network portion = stays the same inside the subnet  
Host portion = numbers that identify specific devices  

Example mask:
255.255.255.0

255 means “fully network.”  
0 means “host numbers go here.”

---

## 4. What Is CIDR Notation? (The /24 thing)

CIDR is simply the number of *network bits*.

Example:
/24 → 24 bits for the network
/26 → 26 bits for the network
/21 → 21 bits for the network


It always comes after the IP:

192.168.10.0/24


The CIDR number **is just a shortcut** for the subnet mask.

Example:
/24 = 255.255.255.0
/21 = 255.255.248.0
/26 = 255.255.255.192


---

## 5. How to Read a Subnet Mask (The Binary Trick)

Each octet has 8 bits.  
Each bit has a “place value”:

128 64 32 16 8 4 2 1


If a bit is 1 → add that value  
If a bit is 0 → skip it

Example:

11100000
= 128 + 64 + 32
= 224


That’s how subnet masks are built.

---

## 6. What Is a Block Size?

This is one of the most important beginner concepts.

**Block size = how far each subnet “jumps”**  
It tells you where the next subnet begins.

Formula:
Block size = 256 - (mask value in the first non-255 octet)


Example:
Mask: 255.255.255.192  
First non-255 octet = 192

256 - 192 = 64


So the subnet boundaries are:

0–63
64–127
128–191
192–255

Example IP: 192.168.1.77
Block size: 64


77 falls inside the **64–127** block:

- Network address: first number → 192.168.1.64  
- Broadcast address: last number → 192.168.1.127  
- Usable range:  
  192.168.1.65 → 192.168.1.126  

Why subtract 1 on each side?
- Network address = can’t be assigned  
- Broadcast address = can’t be assigned  

---

## 8. Host Count

After you subtract the network and broadcast, the usable hosts are:

2^(host bits) - 2


Example:
/26 → 32 - 26 = 6 host bits
2^6 = 64 addresses total
64 - 2 = 62 usable hosts


---

## 9. Why Does Subnetting Matter?

Even if you never do the math by hand again, subnetting helps you:
- understand which devices can talk directly
- understand when traffic needs a router
- avoid overlapping networks (a common cause of outages)
- size cloud networks (AWS VPCs, Kubernetes, etc.)
- read route tables correctly
- troubleshoot connectivity issues

You won’t calculate block sizes every day as a DevOps engineer,
but you will **use the concepts** constantly.

Subnetting is not math —  
it’s about learning how networks “group” things.

# Subnetting Cheat Sheet

A quick reference for common CIDR blocks, their subnet masks, block sizes, 
total addresses, and usable hosts.

| CIDR | Subnet Mask        | Block Size | Total Addrs | Usable Hosts |
|------|---------------------|------------|--------------|---------------|
| /32  | 255.255.255.255     | 1          | 1            | 0             |
| /31  | 255.255.255.254     | 2          | 2            | 0 (special)   |
| /30  | 255.255.255.252     | 4          | 4            | 2             |
| /29  | 255.255.255.248     | 8          | 8            | 6             |
| /28  | 255.255.255.240     | 16         | 16           | 14            |
| /27  | 255.255.255.224     | 32         | 32           | 30            |
| /26  | 255.255.255.192     | 64         | 64           | 62            |
| /25  | 255.255.255.128     | 128        | 128          | 126           |
| /24  | 255.255.255.0       | 256        | 256          | 254           |
| /23  | 255.255.254.0       | 512        | 512          | 510           |
| /22  | 255.255.252.0       | 1024       | 1024         | 1022          |
| /21  | 255.255.248.0       | 2048       | 2048         | 2046          |
| /20  | 255.255.240.0       | 4096       | 4096         | 4094          |
| /19  | 255.255.224.0       | 8192       | 8192         | 8190          |
| /18  | 255.255.192.0       | 16384      | 16384        | 16382         |
| /16  | 255.255.0.0         | 65536      | 65536        | 65534         |

---

## Quick Rules (Easy to Remember)

- Block size = **256 – mask value**  
- Usable hosts = **2^(host bits) – 2**  
- Host bits = **32 – CIDR**  
- Network address = first address of block  
- Broadcast address = last address of block  
- Usable range = (network + 1) → (broadcast – 1)

These are the core rules used throughout DevOps and cloud networking.

