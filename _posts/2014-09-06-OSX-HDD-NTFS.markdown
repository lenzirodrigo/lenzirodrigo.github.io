---
layout: post
title:  "OS X: Mounting external hard drive via terminal"
date:   2014-09-06 10:10:10
comments: true
---
I'm a long time linux([Arch Linux][arch]) & OS X user who likes to use the terminal for everything, and  mounting non `Apple_HFS` partitions on OS X used to give me some problems, so here are the steps to mount a partition and be able to read the content.

Connect your external drive, and open a terminal(I recommend [Iterm2][iterm]):

{% highlight bash %}

~ $ diskutil list 
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *251.0 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            250.1 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *1.0 TB     disk1
   1:                  Apple_HFS WD-Mac                  500.2 GB   disk1s1
   2:                 DOS_FAT_32                         500.0 GB   disk1s2
{% endhighlight %}

According to the information provided by this tool the partition that I want to mount is a `DOS_FAT_32`.
First create the mounting point, I did it in my home:
 
{% highlight bash %}
➜  ~  mkdir mnt
{% endhighlight %}

Now, we can mount the partition there, make sure to use the correct `IDENTIFIER` in your case: 

{% highlight bash %}
➜  ~  sudo mount -t msdos /dev/disk1s2 ~/mnt
Password:
mount_msdos: /dev/disk1s2 on /Users/rodrigo/mnt: Invalid argument
{% endhighlight %}

But using `ntfs` as a file system type mounted that partition:

{% highlight bash %}
➜  ~  sudo mount -t ntfs /dev/disk1s2 ~/mnt
{% endhighlight %}

To unmount the partition just:
{% highlight bash %}
➜  ~  sudo umount /dev/disk1s2
Password:
{% endhighlight %}

And that's all, I hope someone find this usefull.


[arch]:             https://www.archlinux.org/
[iterm]:            http://iterm2.com/
