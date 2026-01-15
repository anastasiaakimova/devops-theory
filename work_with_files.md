# Work with files (edit, copy, move, remove, permissions)

| Category | Command | Description | Examples |
|--------|--------|------------|----------|
| **Editing files** | `nano` | Simple terminal text editor | `nano file.txt` |
|  | `vi / vim` | Advanced text editor | `vim file.txt` |
| **Copying files** | `cp` | Copy files or directories | `cp file.txt /tmp/`|
|   | | | `cp file.txt /tmp/new_name.txt`|
|   | |Copy a directory recursively | `cp -r dir1/ dir2/` |
| **Moving / Renaming files** | `mv` | Move  files and directories | `mv file.txt /tmp/`|
|  |  | Rename files and directories | `mv old.txt new.txt`<br>`mv dir1/ dir2/` |
| **Removing files** | `rm` | Remove files or directories | `rm file.txt`<br>`rm -r dir/`<br>`rm -f file.txt` |
|  | `rmdir` | Remove empty directories | `rmdir empty_dir/` |
| **File permissions** | `chmod` | Change file permissions | `chmod 755 file.txt`<br>`chmod u+w file.txt`<br>`chmod go-rwx file.txt` |
| **Change owner** | `chown` | Change file owner | `chown user file.txt` |
| **Change group** | `chgrp` | Change file group | `chgrp group file.txt` |


## Permissions 
### Numerical Permissions

|  Symbol / Number | Meaning | Example |
|----------------|---------|---------|
|   4 | Read (`r`) | |
|   2 | Write (`w`) | |
|   1 | Execute (`x`) | |
|   0 | --- | No permissions |
|   755 | Owner: rwx, Group: r-x, Others: r-x | `chmod 755 file.txt` |

### Symbolic Permissions
|  Symbol / Number | Meaning | Example |
|----------------|---------|---------|
|  u | User / Owner | |
|   g | Group | |
|   o | Others | |
|   a | All | |
|   + | Add permission | `chmod u+w file.txt` (add write for owner) |
|   - | Remove permission | `chmod go-rwx file.txt` (remove all for group & others) |
|   = | Set exact permission | `chmod u=rw,g=r,o=` |
