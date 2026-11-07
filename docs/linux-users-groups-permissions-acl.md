# Linux Users, Groups and Permissions

## 1. User and Group Management

Created and managed Linux users and groups using:

- `useradd`
- `groupadd`
- `usermod`
- `passwd`
- `id`
- `getent`

Created the `devops` group and the users `devopsuser` and `tester`.

## 2. Linux File Permissions

Practiced permissions management with:

- `chmod`
- `chown`
- `ls -l`

Configured a shared directory at `/opt/devops` with SGID permissions:

```bash
sudo chown root:devops /opt/devops
sudo chmod 2770 /opt/devops
```

## 3. UMASK

Tested:

- `umask 0022`: files 644, directories 755.
- `umask 0002`: files 664, directories 775.

## 4. Access Control Lists (ACL)

Installed the ACL package and practiced:

- `getfacl`
- `setfacl`
- Named user permissions.
- Directory traversal permissions.
- ACL mask and effective permissions.

Example:

```bash
sudo setfacl -m u:devopsuser:rw- /opt/devops/deployment.txt
sudo setfacl -m u:tester:r-- /opt/devops/deployment.txt
```

## 5. ACL Mask Experiment

Restricted the effective permissions of `devopsuser`:

```bash
sudo setfacl -m m::r-- /opt/devops/deployment.txt
```

Verified that reading remained possible while writing was denied.

Restored the mask:

```bash
sudo setfacl -m m::rw- /opt/devops/deployment.txt
```

## 6. Verification

Tested access using:

```bash
sudo -u devopsuser cat /opt/devops/deployment.txt
sudo -u tester cat /opt/devops/deployment.txt
```

Verified that `tester` could read but not modify the file.

## 7. Skills Practiced

- Linux user and group administration
- File and directory permissions
- SGID
- UMASK
- POSIX ACL
- Effective permissions and ACL mask
- Permission troubleshooting
