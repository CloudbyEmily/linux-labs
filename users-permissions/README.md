# Linux Users and Security

## whoami

The `whoami` command is used to display the current user that is logged into the Linux system. It is useful to verify which account you are using before making updates or changes to the system.

## id

The `id` command provides more detailed information about the current user, including the User ID (UID), primary Group ID (GID), and any additional groups the user belongs to. This information helps identify what permissions the user has on the system.

## groups

The `groups` command displays all of the groups that the current user belongs to. Since permissions are often assigned to groups rather than individual users, this command helps determine what level of access a user has.

## root

The root user is the administrator account in Linux and has full control over the operating system. The root user can install software, modify system files, create or delete users, and perform almost any action on the system. Because the root account has unrestricted access, companies avoid logging in as root for everyday tasks whenever possible.

## sudo

If a user has been granted `sudo` privileges, they can temporarily run commands with root (administrator) privileges. This allows users to perform administrative tasks without logging in directly as the root user, which improves security and accountability.

## Principle of Least Privilege

The Principle of Least Privilege means that users are only given the minimum permissions necessary to perform their job responsibilities. This helps reduce security risks by preventing users from accessing or modifying resources they do not need.

## Linux Users vs AWS IAM

Linux users and groups control what a user can do after logging into a Linux system, such as reading files, modifying files, running programs, or restarting services.

AWS Identity and Access Management (IAM) controls what a user can do within an AWS account. For example, an AWS user may be granted permission to launch EC2 instances, create S3 buckets, or view CloudWatch logs. While Linux permissions and AWS IAM are different security systems, they both follow the Principle of Least Privilege by giving users only the permissions they need to perform their job.

## Why Permissions Matter

It is important to understand your permissions and ensure users have the correct level of access. Giving a user more permissions than necessary can create security risks, while giving too few permissions can prevent them from completing their work. Following security best practices helps protect systems while allowing employees to perform their responsibilities efficiently.
