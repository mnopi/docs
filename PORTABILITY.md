#  PORTABILITY 

* **`caller`** Alpine (no)
* **`type -a -p rm`** Zsh (prints the type also)
* **`make`** Alpine (no), Ubuntu Container (no)
* **`man`** Alpine (no), Ubuntu Container (minimize)
```bash
# Alpine 
man 1>/dev/null 2>/dev/null || apk add mandoc man-pages
man tar 1>/dev/null 2>/dev/null || apk add -q --no-progress tar-doc
ls /usr/share/man/man1/tar.1.gz
# Ubuntu Container
man | grep -q unminimize  && yes y | unminimize -qq
rm -rf /etc/dpkg/dpkg.cfg.d/excludes.dpkg-tmp
# No man page 
```
