---
layout: post
title: Setting-Up-A-SSH-Server-On-Kali-Linux
---
<p align="left"><h3 style="text-align: left"><em>Prerequisites</em></h3>
<ul>
<li>PC Running Kali Linux</li><br/>
<li>OpenSSH-Client/Server</li><br/>
<li>DPKG-Reconfigure</li><br/>
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
To make sure our server starts when our system boots, we will add it to our init scripts<br />
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
<p>Navigate to the ssh directory,<br />
root@kali:~# cd /etc/ssh<br />
Then create a directory to store our old keys. You can remove these if you want but we<br />
will store them just incase we ever decide to use them.<br />
root@kali:~# mkdir old_keys<br />
root@kali:~# mv -v *key* old-keys/<br />
</p>
<figure>
<a href="http://programthirteen.com/images/update-keys.png">
        <img src="http://programthirteen.com/images/update-keys.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
