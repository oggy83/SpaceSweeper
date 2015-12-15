Space Sweeper how to setup
====

1. Get external modules using git
2. Build external modules(moyai)
3. Build Space Sweeper game
4. Build backend server
5. Start backend server
6. Start game


### 1. Get external modules using git
Use GitHub's normal procedure. Make sure that you get submodules recursively.
If you're using command line git, you can get appropriate moyai version by this command:

~~~
git submodule update --init --recursive
~~~


### 2. Build external modules(moyai)
See [moyai's README](https://github.com/kengonakajima/moyai) . It supports MacOS X and Windows.

### 3. Build Space Sweeper game
Use ```cl/sswin/sswin.sln``` for windows.
In MacOS X, type ```make depend;make``` in cl directory.

### 4. Build backend server
You can build it on MacOS, Linux. Use make command in vce directory,
and after that make again in sv directory.

### 5. Start backend server
Server program is placed at sv/ssv, and you'll start it with these command line options:

~~~
./ssv realtime database --maxcon=10
~~~

You can see usage text by giving no arguments to the program.

Backend server requires Redis is running at localhost.
You have to install Redis server in your machine and you'll start the redis server
using "redis-server" or some commands like this.

### 6. Start game
In MacOS, you can find "ss" program in cl directory.
In Windows, use sswin.sln and start Debug in Visual Studio.

You have to tell server address to the program.
You can use command line argument like this:

~~~
--dbhost=localhost --rthost=localhost --username=nobita --debug
~~~

When success, you will see character making screen:

![SpaceSweeperCharMake](images/ss_charmake.png)



List of Command Line Parameters
====

- ```--username=STRING ```  Set the user name. This name corresponds to save game data, and needs to be exclusively controlled at a higher directory.
- ```--dbhost=HOSTNAME```  Set the address to the backend server’s database.
Example: "localhost", "192.168.11.2"
- ```--rthost=HOSTNAME``` Set the address to the backend server’s realtime server (for game packet synchronization).
- ```--debug``` Activate debug commands, such as adding items or warping.
- ```--autoplay``` Play automatically. (Stress testing)
- ```--autocharge``` Automatically recharge player energy when playing.
- ```--speedwalk```  Move faster. For debugging.
- ```--infitems``` Infinite items. For debugging.
- ```--jsdebug```  Log the joystick at all times.
- ```--ncloc``` Log nearcast at all times.
- ```--skip-wm``` Skip the world map screen.
- ```--offline``` Play in single-player mode without the backend server.
- ```--fps=NUMBER``` Manually set the frame rate.
- ```--long-db-timeout``` Set the timeout for the database. This is required when playtesting over a slower network, like a wireless LAN.
- ```--save_max_concurrent=NUMBER``` Adjust maximum number of concurrent database saving request sent to backend server. Default value is 128 and this is suitable for SSD servers. Use 5~20 for HDD servers. This also depens on network speed/latency.




















