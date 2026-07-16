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
