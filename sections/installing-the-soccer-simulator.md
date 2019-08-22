# Installation

### Configuring the environment and installing the server and monitor

The following steps were tested and executed using Ubuntu Linux 12.04 and Debian Wheezy 7.

Open a terminal and run:

> sudo apt-get install g++ build-essential libboost-all-dev qt4-dev-tools libaudio-dev libgtk-3-dev libxt-dev bison flex

Go to the Robocup Soccer Simulation official repository [here](https://github.com/rcsoccersim/rcssserver/releases) and download the files rcssserver-x.x.x.tar.gz. Download also the rcssmonitor-x.x.x.tar.gz [here](https://github.com/rcsoccersim/rcssmonitor/releases).
_Note that x.x.x is the downloaded file version._

Extract rcssserver file:
> tar -zxpf rcssserver-x.x.x.tar.gz

Configure and compile rcssserver:
> cd rcssserver-x.x.x
> ./bootstrap
> ./configure && make  
> sudo make install

To install the rcssmonitor, go to the end of this article and follow the same steps to install the soccerwindow2 monitor.

____________________________________________________________________________________

Now you can continue with the installation, either if you're using Ubuntu or Debian:

Go to the Robocup tools repository on SourgeForge by clicking [here](http://en.sourceforge.jp/projects/rctools/releases/).

Download these files:
- librcsc
- agent2d

Currently, the last versions of agent2d and librcsc are: [agent2d](https://osdn.net/projects/rctools/releases/55186) and [librcsc](https://osdn.net/projects/rctools/releases/p3777). Go to the directory where you have saved the downloaded files and follow these steps (do it in this exact order!):  _Note that x.x.x is the downloaded file version._

Open a terminal and extract the files:

> tar -zxpf librcsc-x.x.x.tar.gz  
> tar -zxpf agent2d-x.x.x.tar.gz

**NOTE**: all the directories names where the librcsc files are saved must not contain spaces.

### Installing librcsc

**IMPORTANT:** _Information about all players are written in a log in which the dot(.) is used as decimal separator. Some languages,  as Portuguese, use comma as decimal separator causing an I/O error. 
Your system language must be English. If it is not, run the command `export LC_NUMERIC="C"` on a terminal to avoid any issues._

> cd librcsc-x.x.x/

Run the commands:

**Note:** _If you have permission problems in the first step, instead of_ `./configure` _execute_ `sh ./configure`.

> ./configure  
> make  
> sudo make install

### Installing agent2d

> cd agent2d-x.x.x/

Run: 

> ./configure  
> make  
> sudo make install

### (Optional) Installing the soccerwindow2 monitor

There is another monitor which has more detailed information about matches and players information. This monitor is used in the official Robocup World Cup. If you wish to install it, just run these commands:

In the RoboCup repository cited above in this tutorial, download this [file](https://osdn.net/projects/rctools/releases/p4886).

Open a terminal and run:

> tar -zxpf soccerwindow2-x.x.x.tar.gz  
> cd soccerwindow2-x.x.x.tar.gz   
> ./configure  
> make  
> sudo make install

**Troubleshoot**:

If you got this error (and you probably will):

> unrecognized command line option ‘-pthread-lQtGui’

Open the **configure** file, locate the line below and put a space between $PKG_CONFIG the variables, so it will be like this:

> QT4_LDADD="$($PKG_CONFIG --static --libs-only-other $QT4_REQUIRED_MODULES) $($PKG_CONFIG --static --libs-only-l $QT4_REQUIRED_MODULES)"

Source: http://askubuntu.com/a/892432/664657

### Conclusion

With all done, it is time to run a match and test if everything has done with no errrors. 
See the next tutorial [here](https://github.com/herodrigues/robocup2d-tutorial/blob/master/sections/running-a-match-with-agent2d.md).
