# Linux Processes

## Overview

A process is a running instance of a program. When you start an application or execute a command, Linux creates a process and assigns the process a unique number called the Process ID (PID). Every running process on the system has its own PID so the operating system can easily identify and manage it.

Understanding processes is important because cloud engineers frequently monitor, troubleshoot, and manage running applications on Linux servers.

---

## Program vs. Process

A **program** is an application stored on disk.

Examples:
- Docker
- Python
- Nginx

A **process** is a program that is currently running.

For example:

```bash
python app.py
```

`python` is the program.

When executed, it becomes a running process and Linux will assign a unique PID to it.

---

## Process ID (PID)

Every running process receives a unique Process ID (PID).

The Linux kernel assigns the PID so the operating system can track and manage running processes.

Example:

```
dockerd
PID: 165
```

---

## Viewing Running Processes

Display processes owned by the current user:

```bash
ps
```

Display detailed information about all running processes:

```bash
ps aux
```

Useful information includes:

- USER
- PID
- CPU usage
- Memory usage
- Running command

---

## Running a Background Process

A process can be started in the background by adding an ampersand (`&`).

Example:

```bash
sleep 300 &
```

Linux immediately returns control of the terminal while the process continues running.

---

## Stopping Processes

Gracefully stop a process:

```bash
kill -15 <PID>
```

`SIGTERM` asks the process to shut down safely, allowing it to clean up resources before exiting.

Forcefully stop a process:

```bash
kill -9 <PID>
```

`SIGKILL` immediately terminates the process and should only be used when a process will not respond to normal termination.

---

## Why This Matters

Cloud engineers monitor processes to:

- Troubleshoot application issues
- Stop unresponsive applications
- Verify applications are running
- Identify resource usage
- Maintain healthy Linux servers

---

## Important Takeaway

A process is a running instance of a program. Linux assigns each process a unique PID, allowing administrators to monitor and manage running applications. Commands such as `ps` and `kill` are commonly used to view and control processes during troubleshooting.
