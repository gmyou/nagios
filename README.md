nagios
======

On Nagios Monitoring Server
Now login into your Nagios Monitoring Server. Here you will need to do following things:
  Install the check_nrpe plugin.
  Create a Nagios command definition using the check_nrpe plugin.
  Create Nagios host and add service definitions for monitoring the remote Linux host.
  
Step 1: Install NRPE Plugin
Go to the nagios download directory and download latest NRPE Plugin with wget command.
  [root@tecmint]# cd /root/nagios
  [root@tecmint]# wget http://garr.dl.sourceforge.net/project/nagios/nrpe-2.x/nrpe-2.15/nrpe-2.15.tar.gz
Unpack the NRPE source code tarball.
  [root@tecmint]# tar xzf nrpe-2.15.tar.gz
  [root@tecmint]# cd nrpe-2.15
Compile and install the NRPE addon.
  [root@tecmint]# ./configure
  [root@tecmint]# make all
  [root@tecmint]# make install-daemon

Step 2: Verify NRPE Daemon Remotely
Make sure that the check_nrpe plugin can communicate with the NRPE daemon on the remote Linux host. Add the IP address in the command below with the IP address of your Remote Linux host.
  [root@tecmint]# /usr/local/nagios/libexec/check_nrpe -H <remote_linux_ip_address>
You will get a string back that shows you what version of NRPE is installed on the remote host, like this:
NRPE v2.15
If your receive a plugin time-out error, then check the following things.
Make sure your firewall isn’t blocking the communication between the remote host and the monitoring host.
Make sure that the NRPE daemon is installed correctly under xinetd.
Make sure that the remote Linux host firewall rules blocking the monitoring server from communicating to the NRPE daemon.
