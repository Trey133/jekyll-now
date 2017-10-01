---
layout: post
title: Setting-Up-A-SSH-Server-On-Kali-Linux
---
<p align="left"><h3 style="text-align: left"><em>Prerequisites</em></h3>
<ul>
<li>PC Running Kali Linux</li><br/>
<li>OpenSSH-Client/Server</li><br/>
</ul><br/>
</p>
<h2>Setup</h2>
<p>We will begin this tutorial by making sure we have everything we need to get<br />
our SSH server up and running. Let's go ahead, fire up the terminal and update our system.<br /></p>
<p>root@kali:~# apt-get update</p>
<figure>
<a href="http://programthirteen.com/images/kali-update.png">
        <img src="http://programthirteen.com/images/kali-update.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<br />
<p>Next we are going to install the OpenSSH-Server</p>
<br />
<p>root@kali:~# apt-get install openssh-server</p>
<figure>
<a href="http://programthirteen.com/images/opessh-install.png">
        <img src="http://programthirteen.com/images/openssh-install.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<br />
<p>During the installation process, you should get a dialog that says "Configuring openssh-server".<br />
This will modify the sshd_config file. This file changes how and who can make connections to the server.<br />
If you have already made modifications to this file that you wish to keep, select "keep the local version currently installed".
<br />If you have not made any changes to this file you may choose to "install the package maintainer's version".
<br />This will give you a sshd_config file with default configurations.</p>
<p>Once the installation is finished, it is time to begin setting up our new SSH server.<br />
To make sure our server starts when our system boots, we will add it to our init scripts.</p>
<p>
root@kali:~# update-rc.d ssh remove<br />
root@kali:~# update-rc.d ssh defaults<br />
</p>
<figure>
<a href="http://programthirteen.com/images/update-rc-ssh.png">
        <img src="http://programthirteen.com/images/update-rc-ssh.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>Now our SSH server will start automatically everytime the system starts.<br />
Every openssh-server comes with default encryption keys, so we will go ahead and get rid of those<br />
and generate some new keys.<p>
<p>Navigate to the ssh directory,</p>
<p>root@kali:~# cd /etc/ssh</p>
<p>
Then create a directory to store our old keys. You can remove these if you want but we<br />
will store them just incase we ever decide to use them.</p>
<p>
root@kali:~# mkdir old_keys<br />
root@kali:~# mv -v *key* old-keys/<br />
</p>
<figure>
<a href="http://programthirteen.com/images/update-keys.png">
        <img src="http://programthirteen.com/images/update-keys.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>Now run dpkg-reconfigure to reconfigure our server and generate new encryption keys</p>
<p>root@kali:~# dpkg-reconfigure openssh-server</p>
<figure>
<a href="http://programthirteen.com/images/dpkg-reconf.png">
        <img src="http://programthirteen.com/images/dpkg-reconf.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>You should verify that your keys actually changed with md5sum.</p>
<p>root@kali:~# md5sum ssh_host_*<br />
root@kali:~# md5sum old_keys/ssh_host_*</p>
<p>Let's restart the server with the service command,<br />
and then check to make sure the server restarted correctly.</p>
<p>root@kali:~# service ssh restart<br />
root@kali:~# service ssh status</p>
<figure>
<a href="http://programthirteen.com/images/restart-serv.png">
        <img src="http://programthirteen.com/images/restart-serv.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>Let's see if we can connect to our new server<sup><sup>*The password will be the password of the user you are connecting to*</sup></sup></p>
<figure>
<a href="http://programthirteen.com/images/success.png">
        <img src="http://programthirteen.com/images/sucess.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>You server is now accessable to anyone on the local network!</p>
<p>When you logged in you should have gotten a message like this:</p>
<figure>
<a href="http://programthirteen.com/images/orig-motd.png">
        <img src="http://programthirteen.com/images/orig-motd.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>Let's replace this message with our own personal greeting.<br />
Navigate to the /etc directory and open 'motd' in your text editor.</p>
<p>root@kali:~# cd /etc<br />
root@kali:~# nano motd</p>
<figure>
<a href="http://programthirteen.com/images/mod-motd.png">
        <img src="http://programthirteen.com/images/mod motd.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>Once you are done, save your file and exit. Now we will edit out sshd_config file to make<br />
that our message is displayed when a user logs in. Go to /etc/ssh and open your sshd_config file in your<br />
text editor. Find a line that says "PrintMotd" toward the bottom of the page and change the value<br />
from 'no' to 'yes'. 
<figure>
<a href="http://programthirteen.com/images/print-motd.png">
        <img src="http://programthirteen.com/images/print-motd.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
Then reconnect to your server and see your new message.</p>
<figure>
<a href="http://programthirteen.com/images/new-motd.png">
        <img src="http://programthirteen.com/images/new-motd.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>You do not neccessarily have to edit the sshd_config file to show the motd but I always to ensure that<br />
message is displayed when a user logs in.</p>
<p>That is all for this tutorial. In a future tutorial I will show you how to edit your sshd_config file to allow<br />
only specified users or hosts as well as a few other security related tweaks.</p>
<h5 style="text-align: left">Author: 73RM1N41@Program13</h5>
<h5 style="text-align: left">Date: 09-30-17</h5>
