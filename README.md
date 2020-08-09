<h1>The story about raspberry pi 4, Synology NAS, Mikrotik ac2 and netboot or how to not spend a month trying to make these mthrfckr work</h1> 

Icy fingers gripped my arm in the darkness...
Oh, sorry it's a wrong story!

Well, this started as usual when you have bought a pi. Your first "oh fuck" after sd card is corrupted. 
This brings memories...

So, the goal of this gist is to provide a clear way to setup raspberry pi 4 using NAS to boot via network. Step by step.
Sure there are a lot of articles in the Internet about this but they are all crap (IMHO). Probably except this one
https://www.definit.co.uk/2020/03/pxe-booting-raspberry-pi-4-with-synology-and-ubiquiti-edgerouter/
It was very usefull, however there are few caveates after final steps of the article.

<h4>Synology NAS prerequisites</h4>

* Prepare sd card for rpi as described [in the official page](https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up/2) 
* Enable ssh as described [in section 3](https://www.raspberrypi.org/documentation/remote-access/ssh/)
* Insert card into your rpi4 and start it
* Check that you are able to login using ssh
* RSYNC TBC
* Gracefully shutdown it

<h4>Synology NAS</h4>

You need to enable tftp

![TFTP Settings](/tftp-settings.png)

![TFTP Advanced Settings](/tftp-advanced-settings.png)

<h4>Mikrotik</h4>

In my case you need only one thing - set up one option for dhcp and place it as option or as a part of option set for your dhcp server

![DHCP Option 66](/dhcp-option-66.png)


At that moment you should be able to see a tftp logs on your NAS

![TFTP Logs](/tftp-logs.png)

<h4>cmdline</h4>

<h6>TBC</h6>

<h4>fstab</h4>

<h6>TBC</h6>

<h4>P.S. I'm f...ing idiot</h4>

The initial idea behind rpi is small media server with some usefull things like bitwarden, pivpn and that staff. The easeast way to make it is to use docker.
The installation pretty simple. You just run one line script and voila...

> Error starting daemon: error initializing graphdriver: devmapper: Unable to grow loopback file /var/lib/docker/devicemapper/devicemapper/data: truncate /var/lib/docker/devicemapper/devicemapper/data: file too large

Yo, wtf!

So i spent about a week, desperadly trying to understand what's going on. Of course it was not just wasted time, now i know what's the difference between overlay2 and overlay and othe useful information. I read this https://docs.docker.com/storage/storagedriver/select-storage-driver/

I'm pretty sure that the long version of this story will be much longer than this article. In fact i will have real chance to spend another week or two resolving this issue if my corrupted mind did not suggest me to look at new NAS...and we comes to a short story!

I find this page https://www.synology.com/en-global/knowledgebase/DSM/tutorial/Compatibility_Peripherals/What_kind_of_CPU_does_my_NAS_have

DS216j	<b>Marvell Armada</b> 385 88F6820	Dual Core	2	Yes	Armada38x	DDR3 512 MB

and later

> Never ever "J" - models had Docker because they are NOT Intel x64 based and will never be 
>
> Official forum says

FUUUUUUUUUUUUUUUUUU




<h6>TBC</h6>

