## Major Info ##

This is ONLY a !! Backup Copy to prevent LOST Source CODE !! of original Version as contribute to Andras Retzler! 

All "Hams" and DX Users are very thankful to his hard development work! 

Please SUPPORT his Work by a small donation on "http://sdr.hu" 

1000 Thanks Andras!

The Workarounds i published are ONLY for SMALL Setup's where Problems on CPU LOAD appears! (like Orange-PI-ZERO/old PC's)
I prefer .. LET's keep SIMPLE and REDUCE WIFI/NETWORK BANDWITH/IO + Energy/LOAD for Mobile Connections like GSM/LTE to REDUCE Costs!


### Remark Debian + Python 2.7 ###

The Python 2.7 will be not supported after 12/2019 

But:
- you can go use it on LOCALNET
- use it as subdir protected by BASIC AUTH of Apache
- you can install it inside a virtual server (qemu) to run it inside secure container!ub
- qemu allow hosting of outdated Software on a current Host OS (Host Debian 10/Guest Debian 8)

BEST:
- setup a HOSTAPD+DNSMASQ with OPENWEBRX to get DIRECT WIFI Connect to the SDR-SERVER! WITHOUT a ROUTER/Internet like Home Station (isolated access/ i used a orange-pi-zero-512MB + rtlsdr-v3 + Antenna inside a 5cmx30cm Tube)

Advantages of the old Version:

- With this Version you can run 4 or more INSTANCES / Services on different PORTS! Copy the openwebrx into different directory's (radio1,radio2,radio3...) and at the config file config_webrx.py of them set the DEVICE NUMBER at line:

Sample: config_webrx.py device number = "-d 0 " read rtl_sdr manual!

#### >>> RTL-SDR via rtl_sdr ####
start_rtl_command="rtl_sdr -s {samp_rate} -d 0 -f {center_freq} -p {ppm} -g {rf_gain} -".format(rf_gain=rf_gain, center_freq=center_freq, samp_rate=samp_rate, ppm=ppm)
format_conversion="csdr convert_u8_f"


#### >>> Port at Top Header ####
web_port=8902

- Port 8901 = Dongle 70cm
- Port 8902 = Dongle 80M
- Port 8903 = Dongle 40M
...



### Software Licensing  ###

OpenWebRX is available under Affero GPL v3 license 
(<a href="https://tldrlegal.com/license/gnu-affero-general-public-license-v3-(agpl-3.0)">summary</a>).

OpenWebRX is also available under a commercial license on request. 
- Please contact the Main-Developer Andras Retzler at the address *&lt;randras@sdr.hu&gt;* for licensing options. 

### My Tested Devices ###

Some Workarounds i did to reduce CPU IO on old PCs / Laptops / Tablets / Smartphones:
- Laptops tested: IBM Thinkpd T20,T30,T40,R40,A30P, (Pentium P3, P4, Centrino)
- Mobile Devices: Huawei Y6 2016, Fire Tabletts 7+10 inch. Android 5.1, Iphone SE, Fire TV Stick 1+2 512MB RAM,
- Server tested: Raspi 2,3,4 Odroid N2 4G, Orange PI Zero, Orange PI M2,
- OS tested: Ubuntu, Raspian, Debian

### My Public 4 Channel Test Setup "openwebrx Rig" ###

http://www.websdr-eiterfeld.de 

Location: Center Germany Osthessen Eiterfeld near DB0WAS Wasserkuppe

Channels: 80 Meter, 70cm Meter, ADS-B Flight Radar, 23cm QO100 Oscar 100 Satellite Groundstation

<hr/>


### Waterfall on SmartTV Browser not displayed ###

(NO Mouse Frequency Control on Openwebrx)

Android TV, FireSticks, ...Browsers have broken Javascripts Support

Workaround (no Root required):

- install Firefox of Tablet Version !! by Sideload install (.apk) 
- If on a Firestick or Android TV Box no Mouse Icon with a Tablet Browser is shown then buy a Android Bluetooth Keyboard, Android will now show Mouse Circle for Cursor on TV instead of the TV-Remote Mouse !
..thats it.. Tablet Browsers like Firefox show Waterfall on openwebrx!



### Set Squelch on Start by URL by LINK for Noise Surpressing on Start ###

http://websdr-ip.local/?#sql=40

### openwebrx hangs on Start for 20-30 Sec after OS Upgrade ###

OpenwebRX hang up the Webinterface on Start 20-30 Seconds like a Loop!! 

Then running normal !! Pause on Switch from LSB MODE to USB MODE? 

Then install manual by dpkg -i fftw*.deb ALL fftw3 (fftw3-devel) Packages of 3.3.5 !! as DOWNGRADE on Version 3.3.8 DEFAULT ENABLED CPU-Benchmark-TEST hangs up to 60 seconds on ALL ARM CPU DEVICES (affected RASPIAN Buster, ARMBIAN Buster,Ubuntu 18.XX on Orangepi-zero, Orangepi-H3, Odroid XU,N2,C2 also!!)

Download: https://packages.debian.org/search?keywords=fftw3
<pre>
ii  libfftw3-bin                    3.3.5-3                      armhf        Library for computing Fast Fourier Transforms - Tools
ii  libfftw3-dev:armhf              3.3.5-3                      armhf        Library for computing Fast Fourier Transforms - development
ii  libfftw3-double3:armhf          3.3.5-3                      armhf        Library for computing Fast Fourier Transforms - Double precision
ii  libfftw3-single3:armhf          3.3.5-3                      armhf        Library for computing Fast Fourier Transforms - Single precision
</pre>

I the Bug is now fixed you can set the fftw3 Packages to hold (prevent upgrade)

sudo aptitude hold libfftw3-*

### Reduce openwebrx Server CPU LOAD ###

OpebwebRX reduce CPU Load on small ARM Boards like orangepi-zero? 

Get a clean smooth waterfall.. REDUCE TRAFFIC !!! over 3G/4G

set at config_webrx.py:
<pre>
 ==== DSP/RX settings ====
fft_fps=2
fft_size=4096 #Should be power of 2
fft_voverlap_factor=0.01  #  0.3 default

</pre>

Update: 2020-02-30

### My Workarounds - My Changes ###

Some Workarounds i did to reduce CPU IO (100% to 30% ) and reduce Traffic !! 

on 
- old PCs
- Laptops
- Tablets 
- Smartphones
- SmartTV with Amazon Firestick 1+2 + Firefox Tablet Version!

cause most people use older Hardware to save Money! (Reuse)

### Reduced Client CPU LOAD by INDEX.WRX ###

If your want REDUCE the CPU IO LOAD for older Laptops or PCs edit the index.wrx:

- and remove the LOG-Panel
- Status Panel and the S-Meter-Bar use this custumozed index.wrx (saves 60% CPU Load on older PCs:

[index-wrx-reduced-cpu-load](https://github.com/linuxonlinehelp/openwebrx-workarounds-bugfixes/blob/master/index-wrx-reduced-cpu-load.wrx)

Please report me problems / bugs for free!!

### Supported Hardware QO100 Oscar 100 Satellite ###

- LNB Modified https://remoteqth.com/lnb.php (thanks to Jan)
- Radio Receiver RTL-Dongle: RTL-SDR-V3 https://www.rtl-sdr.com/ 


<hr/>

### Alsa Sound Mixer Noise Blank with Equalizer QASMIXER  ###
create .asoundrc at Client Users Home (Laptop with Alsa) and install: apt-get install qasmixer
the .asoundrc is NOT pre-created on Debian/Ubuntu based Systems!

![Mixer](https://pbs.twimg.com/media/ESrru15XkAAMD57?format=jpg&name=large)

/home/username/.asoundrc
<pre>
pcm.snd_card {
        type hw
        card 0
        device 0
}

ctl.snd_card {
        type hw
        card 0
        device 0
}

ctl.equal {
  type equal
}

pcm.plugequal {
  type equal
  slave.pcm "plughw:0,0"
}

pcm.!default {
  type plug
  slave.pcm plugequal
}
</pre>




### OpenWebRX - Copy of Info Page of Andras ###

OpenWebRX is a multi-user SDR receiver software with a web interface.

----

### ⚠️ From 2019-12-29 OpenWebRX development is discontinued. ⚠️

I'm would like to say a big thanks to everyone who supported me during this project, including those who contributed either code or donations. It has been a very fruitful 6 years, but now it's time to move on to other projects. See also my [blog](https://blog.sdr.hu) about that.  

(@simonyiszk, please keep this GitHub repo for historic purposes.)

Know limitations of the last version:

- Python 2.7, a main dependency of the project, will be not be officially maintained from 1 January 2020. By time, probably it will not be secure to use this version on public servers, unless someone still provides security patches for Python 2. 
- Some specific parts of the DSP code could be improved for better SNR.

Even though these limitations are probably acceptable in an amateur radio project, I would not build critical infrastructure on it.  

For commercial inquiries (e.g. if someone wants me to develop an improved version without these limitations), I'm still open, [drop me an e-mail](mailto:randras@sdr.hu).

----

[:floppy_disk: Setup guide for Ubuntu](http://blog.sdr.hu/2015/06/30/quick-setup-openwebrx.html)  |  [:blue_book: Knowledge base on the Wiki](https://github.com/simonyiszk/openwebrx/wiki/)  |  [:earth_americas: Receivers on SDR.hu](http://sdr.hu/) 

![OpenWebRX](http://blog.sdr.hu/images/openwebrx/screenshot.png)

It has the following features:

- <a href="https://github.com/simonyiszk/csdr">csdr</a> based demodulators (AM/FM/SSB/CW/BPSK31),
- filter passband can be set from GUI,
- waterfall display can be shifted back in time,
- it extensively uses HTML5 features like WebSocket, Web Audio API, and &lt;canvas&gt;,
- it works in Google Chrome, Chromium (above version 37) and Mozilla Firefox (above version 28),
- currently supports RTL-SDR, HackRF, SDRplay, AirSpy and many other devices, see the <a href="https://github.com/simonyiszk/openwebrx/wiki/">OpenWebRX Wiki</a>,
- it has a 3D waterfall display:

![OpenWebRX 3D waterfall](http://blog.sdr.hu/images/openwebrx/screenshot-3d.gif)

**News (2015-08-18)**
- My BSc. thesis written on OpenWebRX is <a href="https://sdr.hu/static/bsc-thesis.pdf">available here.</a>
- Several bugs were fixed to improve reliability and stability.
- OpenWebRX now supports compression of audio and waterfall stream, so the required network uplink bandwidth has been decreased from 2 Mbit/s to about 200 kbit/s per client! (Measured with the default settings. It is also dependent on `fft_size`.)
- OpenWebRX now uses <a href="https://github.com/simonyiszk/csdr#sdrjs">sdr.js</a> (*libcsdr* compiled to JavaScript) for some client-side DSP tasks. 
- Receivers can now be listed on <a href="http://sdr.hu/">SDR.hu</a>.
- License for OpenWebRX is now Affero GPL v3. 

**News (2016-02-14)**
- The DDC in *csdr* has been manually optimized for ARM NEON, so it runs around 3 times faster on the Raspberry Pi 2 than before. 
- Also we use *ncat* instead of *rtl_mus*, and it is 3 times faster in some cases.
- OpenWebRX now supports URLs like: `http://localhost:8073/#freq=145555000,mod=usb`
- UI improvements were made, thanks to John Seamons and Gnoxter.

**News (2017-04-04)**
- *ncat* has been replaced with a custom implementation called *nmux* due to a bug that caused regular crashes on some machines. The *nmux* tool is part of the *csdr* package.
- Most consumer SDR devices are supported via <a href="https://github.com/rxseger/rx_tools">rx_tools</a>, see the <a href="https://github.com/simonyiszk/openwebrx/wiki/Using-rx_tools-with-OpenWebRX">OpenWebRX Wiki</a> on that.

**News (2017-07-12)**
- OpenWebRX now has a BPSK31 demodulator and a 3D waterfall display.

> When upgrading OpenWebRX, please make sure that you also upgrade *csdr*!

## OpenWebRX servers on SDR.hu

[SDR.hu](http://sdr.hu) is a site which lists the active, public OpenWebRX servers. Your receiver [can also be part of it](http://sdr.hu/openwebrx), if you want.

![sdr.hu](http://blog.sdr.hu/images/openwebrx/screenshot-sdrhu.png)

## Setup

OpenWebRX currently requires Linux and python 2.7 to run. 

First you will need to install the dependencies:

- <a href="https://github.com/simonyiszk/csdr">libcsdr</a>
- <a href="http://sdr.osmocom.org/trac/wiki/rtl-sdr">rtl-sdr</a>

After cloning this repository and connecting an RTL-SDR dongle to your computer, you can run the server:

	python openwebrx.py

You can now open the GUI at <a href="http://localhost:8073">http://localhost:8073</a>.

Please note that the server is also listening on the following ports (on localhost only):

- port 4951 for the multi-user I/Q server.

Now the next step is to customize the parameters of your server in `config_webrx.py`.

Actually, if you do something cool with OpenWebRX, please drop me a mail:  
*Andras Retzler, HA7ILM &lt;randras@sdr.hu&gt;*

## Usage tips

You can zoom the waterfall display by the mouse wheel. You can also drag the waterfall to pan across it.

The filter envelope can be dragged at its ends and moved around to set the passband.

However, if you hold down the shift key, you can drag the center line (BFO) or the whole passband (PBS).

## Setup tips

If you have any problems installing OpenWebRX, you should check out the <a href="https://github.com/simonyiszk/openwebrx/wiki">Wiki</a> about it, which has a page on the <a href="https://github.com/simonyiszk/openwebrx/wiki/Common-problems-and-their-solutions">common problems and their solutions</a>.

Sometimes the actual error message is not at the end of the terminal output, you may have to look at the whole output to find it.

If you want to run OpenWebRX on a remote server instead of *localhost*, do not forget to set *server_hostname* in `config_webrx.py`.

## Licensing

OpenWebRX is available under Affero GPL v3 license (<a href="https://tldrlegal.com/license/gnu-affero-general-public-license-v3-(agpl-3.0)">summary</a>).

OpenWebRX is also available under a commercial license on request. Please contact me at the address *&lt;randras@sdr.hu&gt;* for licensing options. 
