Fox-IT's log4j finder compiled as single x86_64 binary for glibc 2.12<br>
Source code: https://github.com/fox-it/log4j-finder <br>
<br>
To reproduce:<br>
- Install centos6<br>
- Edit /etc/yum.repos.d/CentOS-Base.repo \[base\] section. Comment out mirrorlist, set baseurl=https://vault.centos.org/centos/$releasever/os/$basearch/ and sslverify=0 <br>
- yum update <br>
- Install build dependencies: wget curl gcc openssl-devel bzip2-devel<br>
- download Python 3.6.6 build package from https://www.python.org/ftp/python/3.6.6/Python-3.6.6.tgz<br>
- Unzip and run ./configure --enabled-shared --enable-optimizations<br>
- make altinstall<br>
- verify by doing python3.6 -V, you should get the version prompt correctly<br>
- export LD_LIBRARY_PATH=/lib:/usr/lib:/usr/local/lib<br>
- CFLAGS="-std=gnu99" pip3.6 install --user pyinstaller<br>
- git clone https://github.com/fox-it/log4j-finder.git<br>
- cd log4j-finder<br>
- ~/.local/bin/pyinstaller --onefile log4j-finder.spec<br>
