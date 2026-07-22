# TCP vs UDP

## What TCP is

TCP (Transmission Control Protocol) is a form of communication across a network.

TCP ensures that packets of data reach their destination reliably and in the correct order without missing information. It establishes a connection between the sender and receiver, sends the data, verifies that the packets arrive correctly, and retransmits any missing packets if necessary.

Because TCP prioritizes reliability and accuracy, it is commonly used for applications where losing data would cause problems.

Examples include:

* Banking applications
* SSH connections
* Databases
* Online shopping
* Web browsing

Common TCP protocols include:

* HTTP (Port 80)
* HTTPS (Port 443)
* SSH (Port 22)
* MySQL (Port 3306)

---

## What UDP is

UDP (User Datagram Protocol) is also a form of communication across a network.

UDP prioritizes speed over reliability. Unlike TCP, UDP does not establish a connection before sending data and does not confirm whether packets arrived, arrived in the correct order, or arrived at all.

Because UDP has less overhead than TCP, it is faster and is commonly used for applications where speed is more important than perfect delivery.

Examples include:

* Online gaming
* Video streaming
* Voice communication
* DNS queries

Common UDP protocols include:

* DNS (Port 53)
* DHCP (Ports 67 and 68)
* NTP (Port 123)

---

# Key Differences

TCP and UDP are both communication protocols, but they are designed for different purposes.

TCP is used when accuracy and reliability are more important than speed.

UDP is used when speed and low latency are more important than guaranteed delivery.

| TCP                          | UDP                              |
| ---------------------------- | -------------------------------- |
| Connection-oriented          | Connectionless                   |
| Reliable delivery            | No delivery guarantee            |
| Confirms packets arrive      | Does not confirm packets arrive  |
| Retransmits lost packets     | Does not retransmit lost packets |
| Packets arrive in order      | Packets may arrive out of order  |
| More overhead                | Less overhead                    |
| Used for web, SSH, databases | Used for gaming, streaming, DNS  |

---

# Preschool Analogy

Imagine sending a drawing to your teacher.

## TCP

You hand your teacher each page and ask:

"Did you receive page 1?"

Teacher:

"Yes."

You send page 2.

Teacher:

"Yes."

If page 3 gets lost, you send it again.

TCP makes sure everything arrives correctly.

---

## UDP

You throw all the pages toward your teacher at once.

Some pages arrive.

Some might get lost.

You do not stop to check.

UDP is faster because it does not spend time confirming delivery.

---

# Cloud Engineering Use Cases

Cloud engineers use TCP and UDP every day when deploying, troubleshooting, and maintaining cloud infrastructure.

Examples include:

* Verifying that web servers are listening on TCP ports 80 or 443.
* Troubleshooting SSH connectivity on TCP port 22.
* Confirming that databases are accepting TCP connections.
* Troubleshooting DNS queries that use UDP port 53.
* Checking whether firewalls, Security Groups, or Network ACLs are blocking network traffic.

Understanding TCP and UDP helps cloud engineers determine whether a problem is caused by the application, network configuration, or security rules.

---

# Commands Used During the Lab

## ss -tuln

Displays all listening TCP and UDP ports without resolving hostnames.

Purpose:

* Verify which services are accepting network connections.
* Identify which ports are open and listening.
* Troubleshoot networking issues.

---

# Lab Observations

Command:

```bash
ss -tuln
```

Output:

```text
udp   UNCONN   0   0   0.0.0.0:68
```

Observations:

* Only one listening service was found.
* The service is using UDP.
* Port 68 is used by the DHCP client.
* `0.0.0.0` means the service is listening on all available network interfaces.
* No TCP services were running at the time of the lab.

---

# Troubleshooting Notes

If a web application cannot be reached:

1. Verify the application is running.
2. Check whether the expected TCP or UDP port is listening.
3. Confirm the firewall, Security Group, or Network ACL allows the required traffic.
4. Review application logs for errors.
5. Test network connectivity.

Troubleshooting flow:

```text
User reports an issue
        │
        ▼
Understand the problem
        │
        ▼
Is the application running?
        │
        ▼
Review logs
        │
        ▼
Is the application listening on the correct TCP/UDP port?
        │
        ▼
Test network connectivity
        │
        ▼
Check firewall / Security Groups / Network ACLs
        │
        ▼
Verify the required traffic is allowed
        │
        ▼
Apply the correct fix
        │
        ▼
Retest
        │
        ▼
Confirm with the user
```
