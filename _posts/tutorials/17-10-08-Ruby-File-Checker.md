---
layout: post
title: Ruby-File-Checker
---
<p>Today I am going to show you how to create a simple file checker with Python.<br />
We will be checking the files name, existence, path, type, creation/modification dates,<br />
permissions, and size.</p>
<p align="left">Prerequisites</p>
<ul style="text-align: left">
<li>I will be using Kali but any Linux Distro should work.* <sup><sup>I have not tested anything other than Kali</sup></sup></li><br /><br />
<li>Ruby <sub>apt-get install ruby</sub> <sup>I will be using version 2.3.3p222</sup></li><br /><br />
</ul>
</p>
<p>Let's begin by adding our standard Ruby header<br />
{% highlight ruby %}
#!/usr/bin/ruby -w
{% endhighlight %}
We will add the '-w' option to turn on warnings for our Ruby script.<br />
Having a file checker can be very useful at times, but if the program must run interactively,<br />
it suddenly becomes less attractive to those serious systems admins and developers out there<br />
who want results, and they want 'em now...</p>
<p>So what we are going to do is allow the user to pass a filename as an argument to our program,<br />
from the terminal and have the program output the data to stdout. That way the user can get their data<br />
quickly and get on with there work.</p>
<p>To do this we are going to use 'ARGV.each'<br />
{% highlight ruby %}
# Allow User To Parse File From Command Line
ARGV.each { |filename|
{% endhighlight %}
<p>The first thing we want to check for when a user passes the filename, is whether or not they need<br />
help using our program. We can check for this with a simple conditional.</p>
{% highlight ruby %}
# Check To See If User Is Asking For Help
if filename == '--help' || filename == '-h'
  puts "Usage: flck [file/dir]"
{% endhighlight %}
<p>If, however, our user doesn't need help, the first thing we want to do is to check and see if<br />
the file exists that they are asking about. We will do this using the 'File::exist?' function.</p>
{% highlight ruby %}
# If File Exists, Run Remaining Tests
# Else Skip To End
  if File::exist?( filename )
    file = File.open( filename )
{% endhighlight %}
<p>Here we are telling Ruby that if the file exists, open it, and if the file does not exist, skip<br />
to the end of the script.<br />
The next thing we want to do is to find out whether the filename provided by the user is an actual<br />
file or if it is a directory instead. We can do that by adding the following to our script:<br />
{% highlight ruby %}
# Check To See If File Name Is An Existing File
    if File.file?( file )
      chkfile = "True"
    else
      chkfile = "False"
    end
# Check To See If File Name Is An Existing Directory
    if File::directory?( file )
      dir = "True"
    else
      dir = "False"
    end
{% endhighlight %}
<p>Now that we know whether or not the filename is actually a file, let's check to see<br />
what kind of permissions we have. We want to know if we can read, write, or execute the file.<br />
We can find out like this:<br />
{% highlight ruby %}
# Check File Permissions
# Check To See If File Is Readable
    if File.readable?( file )
      readable = "True"
    else
      readable = "False"
    end
# Check To See If File Is Writable
    if File.writable?( file )
      writeable = "True"
    else
      writeable = "False"
    end
# Check To See If File Is Executable
    if File.executable?( file )
      exec = "True"
    else
      exec = "False"
    end
{% endhighlight %}
<p>So, now we know if the filename supplied by the user is a file or a directory, and we also know<br />
what we are allowed to do with the file. Let's check to see if the file contains any data.</p>
{% highlight ruby %}
# Check To See If File Is Zero Size
    if File.zero?( file )
      zerosize = "True"
    else
      zerosize = "False"
    end
{% endhighlight %}
<p>Next we are going to check to see where the file is located, how big the file actually is,<br />
and what type of file it is (ex: .pdf, .mp3, .docx).</p>
{% highlight ruby %}
# Check File Path
    path = File::expand_path( file ).to_s
# Check File Size
    size = File.size?( file ).to_s
# Check File Type
    ftype = File::ftype( file )
{% endhighlight %}
<p>The final 3 things we are going to check for is to see when the file was created, when it was<br />
last modified, and when it was last accessed.</p>
{% highlight ruby %}
# Check To See When File Was Created
    create = File::ctime( file ).to_s
# Check to See When File Was Last Modified
    mod = File::mtime( file ).to_s
# Check To See When File Was Last Accessed
    lstaccess = File::atime( file ).to_s
{% endhighlight %}
<p>Now that we have collected all of the data we need for our report, lets tell our script how it<br />
should be presented to the user. This is just my version of this, you can modify it to present <br />
the data however you'd like.</p>
{% highlight ruby %}
# Print Output Of Tests To Screen
    puts "##################################################"
    puts "#  [Name]: "+ filename
    puts "#  [Exsisting File]: "+ chkfile
    puts "#  [Exsisting Directory]: "+dir
    puts "#  [Path]: "+path
    puts "#  [File Type]: "+ftype
    puts "#  [Created]: "+create
    puts "#  [Modified]: "+mod
    puts "#  [Last Accessed]: "+lstaccess
    puts "#  [Readable]: "+readable
    puts "#  [Writeable]: "+writeable
    puts "#  [Executable]: "+exec
    puts "#  [Zero Size]: "+zerosize
    puts "#  [Size]: "+size
    puts "##################################################"
{% endhighlight %}
<p>Now that we have finished all of that, we need to tell Ruby what to do if the filename<br />
provided by the user, did not exist. Then we will tell Ruby that we are finished.</p>
{% highlight ruby %}
  else
# If The File Does Not Exist
# Print Error Message
    print "That File Does Not Exist!!!\n"
  end
end
}
{% endhighlight %}
<P>Now you've got your very own Ruby file checker. Save it as filecheck and add execute permissions.<br />
then run your new program with './'</p>
{% highlight bash %}
chmod +x filecheck
./filecheck --help
Usage: flck [file/dir]
./filecheck filecheck
##################################################
#  [Name]: filecheck
#  [Exsisting File]: True
#  [Exsisting Directory]: False
#  [Path]: /root/Development/RubyDev/filecheck
#  [File Type]: file
#  [Created]: 2017-10-08 15:34:09 -0500
#  [Modified]: 2017-10-08 15:34:03 -0500
#  [Last Accessed]: 2017-10-08 15:34:18 -0500
#  [Readable]: True
#  [Writeable]: True
#  [Executable]: True
#  [Zero Size]: False
#  [Size]: 2326
##################################################
{% endhighlight %}
<p>I hope you enjoyed this tutorial! Stay tunned there's lots more to come.</p>
<p align="left">Author: 73RM1N41@Program13</p>
