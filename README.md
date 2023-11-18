## RHEL Part-1

# Access Command Line Interface

<h2>Introduction to Bash Shell</h2>
<h3>Shell Prompt</h3>
<p>"$" in prompt shows that it is normal/regular user<br>"#" in prompt tells that shell is working with root user</p>

<pre>[diwakar@dev ~]$</pre>

<u>Redhat recommeds to use default shell which is BASH</u>

<h3>Command Synatx</h3>
<p>Each command consists/may consist of three parts</p>
<ul>
  <li>Command</li>
  <li>Options (To define behaviour of Command)</li>
  <li>Arguments to feed into command</li>
</ul>

<pre>[diwakar@dev ~]$ ls -la .</pre>
<ul>
  <li>Command : ls (To list files)</li>
  <li>Options : la (long list and show hidden files)</li>
  <li>Arguments : '.' (files to list in current pwd)</li>
</ul>

<h3>Execute and Write simple commands in Command Line</h3>
<p>To execute to commands : command1;command2</p>
<pre>
[diwakar@dev ~]$ whoami;uptime
diwakar
 12:20:51 up 51 min,  2 users,  load average: 0.00, 0.00, 0.00
</pre>
<p>Some more commands</p>
<pre>
[diwakar@dev ~]$ # date command prints system date sync with chronyd
[diwakar@dev ~]$ date
Sat Nov 18 12:25:26 PM EST 2023
[diwakar@dev ~]$ date +%X
12:25:35 PM
[diwakar@dev ~]$ date +%R
12:25
[diwakar@dev ~]$ date +%r
12:25:40 PM
[diwakar@dev ~]$ date +%x
11/18/2023
[diwakar@dev ~]$ # file command uses first two bytes compiled file header to determine type
[diwakar@dev ~]$ file .ssh
.ssh: directory
[diwakar@dev ~]$ file .viminfo
.viminfo: ASCII text
</pre>
<h3>Viewing Contents of File</h3>
<h4>Using cat to get contents of file,create and modify small files</h4>
<p>cat command helps to create,view ,modify file contents,generally for files with smaller contents</p>
<pre>
<code>
[diwakar@dev ~]$ cat .bashrc
# .bashrc

#Source global definitions
if [ -f /etc/bashrc ]; then
. /etc/bashrc
fi
[diwakar@dev ~]$ touch file1 file2
[diwakar@dev ~]$ echo "this is file1" >> file1
[diwakar@dev ~]$ echo "this is file2" >> file2
[diwakar@dev ~]$ cat file1 file2
this is file1
this is file2
</code>

</pre>
<h4>Viewing page-wise display using "more "less commands</h4>
<p>Page wise display helps for longer outputs to render in pages</p>
<pre>
[diwakar@dev ~]$ # less command provides page-wise display for longer output's and UP and DOWN arrows for browsing pages
[diwakar@dev ~]$ # using 'q' to quit
[diwakar@dev ~]$ # wc command to count no characters(c),words(w),lines(l) occurrances in a file
[diwakar@dev ~]$ wc -l /etc/passwd
30 /etc/passwd
</pre>
<h3>Tab Completion</h3>
<p>Help to finish command using TAB.ESC+. helps to finish your argument with last written argument</p>
<pre>
[diwakar@dev ~]$ # Understanding TAB Completion
[diwakar@dev ~]$ # chmTABTAB provides list of cmd's starts with chm and chmTAB finishes command
[diwakar@dev ~]$ chm
chmem  chmod
[diwakar@dev ~]$ ls /etc/pa
pam.d/   passwd   passwd-
[diwakar@dev ~]$ usermod --
--add-subgids   --badnames      --del-subuids   --groups        --inactive      --move-home     --prefix        --shell
--add-subuids   --comment       --expiredate    --help          --lock          --non-unique    --root          --uid
--append        --del-subgids   --gid           --home          --login         --password      --selinux-user  --unlock

</pre>
<h3>Writing long commands on multiple lines</h3>
<p>Use \ escapes the empty tab on to next line prefixed with ></p>
<pre>
[diwakar@dev ~]$ head -n3 /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
[diwakar@dev ~]$ tail -n3 /etc/passwd
systemd-oom:x:984:984:systemd Userspace OOM Killer:/:/usr/sbin/nologin
systemd-resolve:x:983:983:systemd Resolver:/:/usr/sbin/nologin
diwakar:x:1000:1000::/home/diwakar:/bin/bash
[diwakar@dev ~]$ tail -n3 \
> /etc/passwd
systemd-oom:x:984:984:systemd Userspace OOM Killer:/:/usr/sbin/nologin
systemd-resolve:x:983:983:systemd Resolver:/:/usr/sbin/nologin
diwakar:x:1000:1000::/home/diwakar:/bin/bash
</pre>
<h3>Getting history of our Command Lines</h3>
<p>Viewing history or your command trail helps to track incase of debugging and troubleshooting</p>
<pre>
[diwakar@dev ~]$ # history command provides ur commands trail in shell
[diwakar@dev ~]$ # !number finishes your command in history
[diwakar@dev ~]$ # !string finishes your command based on your provided string
[diwakar@dev ~]$ # !! executes you last or previously executed command
[diwakar@dev ~]$ !!
cat /etc/passwd
</pre>
<h3>Navigating RHEL File System</h3>
<pre>
[diwakar@dev /]$ ls
afs  bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
</pre>
<table>
<tr>
  <th><b>Path</b></th>
  <th><b>What it Conatins</b></th>
</tr>
<tr>
  <td>/boot</td>
  <td>Files to start the boot process</td>
</tr>
<tr>
  <td>/dev</td>
  <td>Special device file sthat system uses to access h/w</td>
</tr>
<tr>
  <td>/etc</td>
  <td>System specific configuration files</td>
</tr>
<tr>
  <td>/home</td>
  <td>Contain directories - user specific</td>
</tr>
<tr>
  <td>/run</td>
  <td>Runtime specific data since last reboot</td>
</tr>
<tr>
  <td>/tmp</td>
  <td>A world accessible folder where retention closes to 10 days</td>
</tr>
<tr>
  <td>/usr,/usr/bin,/usr/sbin</td>
  <td>installed s/w,shared lib,system specific bin</td>
</tr>
<tr>
  <td>/var</td>
  <td>System specific variable daa that persists between boots</td>
</tr>
</table>

<h3>Managing Files from Command Line</h3>
