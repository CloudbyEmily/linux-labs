# Linux Networking Fundamentals

## What is an IP Address?

An IP address is a unique network address assigned to a device so it can send and receive data over a network. Similar to a house being given a unique mailing address so it can send and receive mail, every device needs an IP address so other devices know where to send information.

## Public vs. Private IP Addresses

### Public IP Address

A public IP address is visible and reachable from the internet. Devices with a public IP can communicate with other devices over the internet, provided firewalls or security rules allow the connection.

### Private IP Address

A private IP address is assigned to a device on a private network, such as a home Wi-Fi network, a company network, or an AWS Virtual Private Cloud (VPC). Private IP addresses are not directly accessible from the internet, making them more secure for internal communication.

## What is Localhost?

Localhost is the address a computer uses to communicate with itself. The loopback address `127.0.0.1`, commonly referred to as `localhost`, allows programs running on the same computer to communicate without sending traffic over the network.

## Useful Linux Networking Commands

### `hostname -I`

Displays the IP address(es) currently assigned to your computer.

### `ip addr`

Displays detailed information about your computer's network interfaces, including their IP addresses and current status.

### `ping localhost`

Tests whether your computer can communicate with itself by sending network packets to the loopback address. A successful response confirms that the local networking stack is functioning properly.
# Linux Network Interfaces

## What is a Network Interface?

A network interface is the connection point that allows a computer to communicate over a network. A computer can have multiple network interfaces for different types of network traffic.

### Common Network Interfaces

### lo

The loopback (localhost) interface.

- Represents the computer communicating with itself.
- Uses the IP address 127.0.0.1.
- Traffic never leaves the computer.

### eth0

A network interface that connects a computer to a network.

- Often represents the primary network connection.
- On cloud servers like AWS EC2, this is usually a virtual network interface.
- Receives and sends network traffic to other computers.

### docker0

A virtual network interface created by Docker.

- Allows Docker containers to communicate with each other and with the host machine.
- Commonly uses the 172.17.x.x network.

## Using `ip addr`

The `ip addr` command displays:

- Network interfaces
- IP addresses
- Interface status (UP or DOWN)
- IPv4 and IPv6 addresses

Cloud engineers commonly use this command to verify that a server has the correct network configuration when troubleshooting connectivity issues.

---

# Network Ports

## What is a Port?

A port identifies which application or service should receive network traffic after it reaches a computer.

Think of it like an apartment building.

- The IP address gets the package to the correct building.
- The port number tells the mail carrier which apartment should receive the package.

Without ports, a computer would not know whether incoming traffic belongs to a web server, an SSH server, or a database.

## Common Ports

| Port | Service | Purpose |
|------|---------|---------|
| 22 | SSH | Secure remote access to Linux servers |
| 80 | HTTP | Unencrypted web traffic |
| 443 | HTTPS | Secure web traffic |
| 53 | DNS | Domain name resolution |
| 3306 | MySQL | MySQL database connections |
| 5432 | PostgreSQL | PostgreSQL database connections |

## Using `ss -tuln`

The `ss -tuln` command displays:

- TCP listening ports
- UDP listening ports
- Local IP addresses
- Port numbers

Cloud engineers use this command to verify that applications are listening on the expected ports.

## Why Cloud Engineers Check Listening Ports

Checking listening ports helps determine whether an application is ready to receive network traffic.

For example, if a web server should be accepting HTTPS traffic on port 443 but nothing is listening on that port, users will not be able to reach the website even if the server is running.

Viewing listening ports is a common step when troubleshooting application and network connectivity issues.
# DNS Basics

## What is DNS?

DNS (Domain Name System) translates human-readable domain names into IP addresses that computers use to communicate.

Example:

google.com → IP address

## Using ping for DNS Testing

The ping command can show whether a domain name successfully resolves to an IP address.

Example:

ping -c 2 google.com

If DNS works, the output will display the resolved IP address.

Cloud engineers use DNS troubleshooting to determine whether problems are caused by name resolution, networking, or application issues.

## Troubleshooting Lesson

A website can fail because of different layers:

1. DNS problem
2. Network connectivity problem
3. Port/firewall problem
4. Application/service problem

Understanding where the failure occurs helps cloud engineers troubleshoot efficiently.
# Cloud Engineer Troubleshooting Flow

When a user reports that a website is unavailable, cloud engineers troubleshoot by identifying which layer of the system is failing.

## Troubleshooting Layers

### 1. DNS

Question:

"Is the domain name pointing to the correct destination?"

Possible issues:

- DNS record not updated
- Domain pointing to the wrong server
- DNS resolution failure

Tools:

```bash
nslookup domain.com
dig domain.com
ping domain.com
