* Remove all comments and spaces from a file

                        cat /etc/httpd/conf.d/ssl.conf | grep -v "#" | sed '/^$/d'

* Comment

                        sed -i 's/^/#/g' /example/file/here.txt

* Uncomment
 
                        sed -i 's/^#//g' /example/file/here.txt

* Manipulate a varibale

                        website=$(sed 's|/|\/|g' <<< $website)

* Log as sshd using bash to check if sshd can open `authorized_keys`

                       su - sshd -s /bin/bash 

* Create a dummy file with a given size on the disk:

                       fallocate -l 40G /tmp/a

* symlinks

                       ln -sf /path/to/file /path/to/symlink

* RAM

                       free -g

* Disk 
  
		       lsblk

* CPU cores
                       lscpu (multiply Sockets \* Cores per socket)

* abourt command after some time 

                       timeout 5 My_command

* size of a path

                       du -sh path/to/folder/or/file

* Get out of stuck terminal

                       entre ~.


## Package manager

* Install local rpms

                      yum localinstall
                      rpm -ivh package.rpm

* search packages

                      yum search ldap

* Clear cache 

                      yum clean all

## IO 

_You cannot safely write to a file while reading, it is better to read the file into memory, update it, and rewrite it to file._

```bash
with open("file.txt", "r") as in_file:
buf = in_file.readlines()

with open("file.txt", "w") as out_file:
for line in buf:
if line == "; Include this text\n":
line = line + "Include below\n"
out_file.write(line)
```
