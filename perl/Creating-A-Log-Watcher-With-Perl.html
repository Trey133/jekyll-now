---
layout: post
title: Creating-A-Log-Watcher-With-Perl
---
<p>Today I am going to show you how to create a Linux log watcher with Perl.<br />
I would like to note in advance that this is one of many ways to do this. You may know of<br />
a better way. If this is the case, we would certainly love to hear about it. Send an email<br />
to the address at the bottom of this page or just . </p>
<h3 style="text-align:left">Prerequisites</h3>
<div class="prequisites">
<ul style="text-align: left">
<li>I will be using Kali Linux but any Linux Distro Should Work.</li><br /><br />
<li>Perl5 (I will be using v5.26.0)</li><br /><br />
</ul>
</div>
<p>Let's begin by adding our header. Then we will tell Perl that we want to use ANSIColor. We are using this to<br />
easily distinguish the different logs by color coding them.</p>
<figure>
<a href="http://programthirteen.com/images/perlog-header.png">
        <img src="http://programthirteen.com/images/perlog-header.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>The next thing we are going to do, is define how quickly our logwatcher switches between log files.<br />
We don't want our logwatcher to rotate through the files too quickly because we won't have time to read them, but if<br />
it rotates too slowly, it becomes useless as we could manually look at our files fairly quickly.<br />
You can play with this variable a little bit to see what is comfortable for you.</p>
<figure>
<a href="http://programthirteen.com/images/perlog-speed.png">
        <img src="http://programthirteen.com/images/perlog-speed.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>Now that we have our speed variable defined, let's move on to our actual logs.<br />
You can find most of your system log files in your '/var/log/' directory. Go there now and see which logs you<br />
would like to add to your script. Once you have decided which logs you are going to have your script watch,<br />
head back over to your editor and tell your script what your log files are. The great thing about Perl is, it's<br />
really easy to store the output of terminal commands as variables. So this is how we are going to display our logs.<br /></p>
<figure>
<a href="http://programthirteen.com/images/define-logs.png">
        <img src="http://programthirteen.com/images/define-logs.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>I am going to use 'journalctl', which isn't one of my system logs, it's actually a logwatcher itself, but it can still be used,<br />
and I am also going to display my 'ufwlog', which is the log that tracks the activity of my firewall.</p>
<p>As you can see on line 4 of my file, I am adding my logfiles in a for loop. I am doing this so that I can prevent<br />
the script from terminating after it cycles through the logs the first time. I also added a function call 'clear()'.<br />
This is going to clear the screen after every log so that we don't wind up with a cluttered mess. We will define this<br />
function later on.</p>
<p>Now we are going to tell our script to display our logs. We are also going to be adding some color, be sure to make<br />
each log a different color. You can see that I also added a 'sep()' function. This is going to act as the seperator<br />
between the title of our log and the actual log itself. You don't have to add this but you will have a cleaner output if you do.<br />
our 'sleep(x)' function is going to make our program wait for 'x' seconds. Now we can change 'x' at the top of<br />
our file to easily change the speed of the entire script.</p>
<figure>
<a href="http://programthirteen.com/images/show-logs.png">
        <img src="http://programthirteen.com/images/show-logs.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>The last thing we need to do is define our 'clear' and 'sep' functions.</p>
<figure>
<a href="http://programthirteen.com/images/def-funcs.png">
        <img src="http://programthirteen.com/images/def-funcs.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>That's It.<br />
Now just save your file as perlog.pl and give it execute permissions with 'chmod +x perlog.pl'.<br />
Now you can execute your new log watcher with './'<br />
EX: ./perlog</p>
<figure>
<a href="http://programthirteen.com/images/running-perlog.png">
        <img src="http://programthirteen.com/images/running-perlog.png" alt="" height="500px" width="750px"/>
    </a>
</figure>
<p>Edit your script to add or remove any logs you would like. You can also add terminal commands that you would like to watch the same way we added 'journalctl'<br />
earlier. Modify until it's perfect for you and as always, if you know of a 'better' way, post it in the comments or shoot us an email from the link at the bottom of the page.</p>
<p align="left">Author: 73RM1N41@Program13</p>
