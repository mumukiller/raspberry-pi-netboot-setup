<h1>The story about raspberry pi 4, Synology NAS, Mikrotik ac2 and netboot or how to not spend a month trying to make these mthrfckr work</h1> 

Icy fingers gripped my arm in the darkness...
Oh, sorry it's a wrong story!

Well, this started as usual when you have bought a pi. Your first "oh fuck" after sd card is corrupted. 
This brings memories...

So, the goal of this gist is to provide a clear way to setup raspberry pi 4 using NAS to boot via network. Step by step.
Sure there are a lot of articles in the Internet about this but they are all crap (IMHO). Probably except this one
https://www.definit.co.uk/2020/03/pxe-booting-raspberry-pi-4-with-synology-and-ubiquiti-edgerouter/
It was very usefull, however there are few caveates after final steps of the article.


Mikrotik
In my case you need only one thing - set up one option for dhcp
![GitHub Logo](/dhcp-option-66.png)


TBC
