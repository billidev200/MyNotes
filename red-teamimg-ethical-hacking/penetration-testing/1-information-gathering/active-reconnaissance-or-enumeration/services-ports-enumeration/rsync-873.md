# Rsync/873

**Rsync** (short for _remote sync_) is a **file synchronization and transfer tool**. It’s widely used on Unix/Linux systems to copy files between machines, back up directories, and mirror servers.

#### 🔑 Key points about rsync:

* **Default port:** `873/tcp` (but can also run over SSH).
* **Purpose:** Efficiently synchronize files and directories by only transferring the changes (not the whole file).
* **Common uses:**
  * Backup solutions.
  * Mirroring web servers.
  * System migrations.

| Feature            | **rsync**                                                    | **SMB**                                           |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------- |
| **Port**           | 873 (daemon mode), or SSH (22)                               | 445 (modern), 139 (older NetBIOS)                 |
| **OS**             | Primarily Linux/Unix                                         | Primarily Windows                                 |
| **Purpose**        | Fast file synchronization & backups (syncs only differences) | General-purpose file & printer sharing            |
| **Authentication** | Can be public (no auth) or require credentials               | Usually requires Windows accounts or guest access |
| **Enumeration**    | `rsync target::` to list modules                             | `smbclient -L //target/` to list shares           |

## Enumeration

```
rsync rsync://target
rsync rsync://target/ Share we found to view
rsync -av rsync://target1.ine.local/SHARE  - To download the file
```

View shares

```
rsync rsync://target
```

Open Share

```
rsync rsync://target/ Share we found to view
```

Download File

```
rsync -av rsync://target1.ine.local/SHARE/ .   - To download the file
```

* Tahe current local directory (`.`)
* **Archive mode** (`-a`) to preserve file properties
* &#x20;**Verbose mode** (`-v`) for detailed output.

Metasploit Scanner

```
auxiliary/scanner/rsync/modules_list
```
