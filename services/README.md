# Linux Services

## Overview

A service is a program that runs in the background to perform a specific job on a Linux system. Many applications, such as web servers, databases, and container platforms, run as services so they can start automatically and continue running without user interaction.

Cloud engineers regularly manage services to ensure applications remain available and operating correctly.

---

## What is systemd?

`systemd` is the service manager used by many modern Linux distributions.

It is responsible for:

- Starting services
- Stopping services
- Restarting services
- Monitoring running services
- Starting services automatically when the system boots

Think of `systemd` as the manager responsible for keeping important services running.

---

## Checking Service Status

View the status of a service:

```bash
systemctl status <service-name>
```

Example:

```bash
systemctl status docker
```

This command displays information such as:

- Whether the service is active or failed
- When the service started
- The Main PID
- Recent log messages

---

## Service Status

A service may appear as:

**Active (running)**

The service is currently running.

**Inactive**

The service is stopped.

**Failed**

The service encountered an error and stopped running.

---

## Viewing Logs

Linux systems using `systemd` store logs in the system journal.

View recent log entries:

```bash
journalctl -n 20
```

View logs for a specific service:

```bash
journalctl -u <service-name>
```

Logs help engineers determine:

- What happened
- When did it happened
- Which service reported the event
- Whether errors or warnings occurred prior to the crash or fail

---

## Basic Troubleshooting Workflow

When a user reports that an application is not working:

1. Check the service status and identify the PID.

```bash
systemctl status <service-name>
```

2. Review the logs.

```bash
journalctl -u <service-name>
```

3. Determine the root cause.

4. Fix the issue if necessary.

5. Restart the service if appropriate.

```bash
systemctl restart <service-name>
```

6. Verify the service is healthy.

```bash
systemctl status <service-name>
```

While a service that is NOT running clearly tells us the application is not functioning correctly, a service that absolutely is running does not always mean the application is functioning correctly. Reviewing logs helps identify errors that are not visible from the service status alone.

---

## Why This Matters

Cloud engineers use services and logs to:

- Troubleshoot production issues
- Investigate application failures
- Monitor server health
- Restore applications after failures
- Verify services are operating correctly

---

## AWS Connection

Many AWS workloads run as Linux services on EC2 instances.

Examples include:

- Docker
- Nginx
- Apache
- PostgreSQL
- MySQL

Understanding how to manage services, like the ones listed above, in Linux prepares engineers to troubleshoot cloud-hosted applications.

---

## Important Takeaway

A service is a long-running background program managed by `systemd`. During troubleshooting, I first verify the service status with `systemctl`, then review logs using `journalctl` to identify the root cause before restarting or repairing the service if needed.
