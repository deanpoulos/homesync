# Todo

- [ ] Add config file
- [ ] Add man page

# Description

A tool for syncing specified directory structures between machines 
on the same network.

# Usage

``` console
$ homesync --help
Usage: homesync [ --help | -h ] [ --list -l ] [ --menu | -m ]
                [ --src | -s ] source_path_to_file
                [ --dst | -d ] destination_path

   pull     Pull changes from remote machine on LAN to local.
   push     Push changes from local machine to remote on LAN.

Options:

   --help -h  Display this menu.
   --list -l  Lists nodes on LAN with open ssh ports.
   --menu -m  Select remote IP from menu of all available IPs.
   --src -s   Path to directory from which files will be synced.
   --dst -d   Path from directory to which files will be synced.
```

# Example

``` console
$ homesync -l
Searching LAN for open ssh ports... done!

192.168.0.74
192.168.0.51
192.168.0.22

$ mkdir -p some_dir/some_other_dir
$ homesync -ms some_dir -d ~/ push
Searching LAN for open ssh ports... done!

1) 192.168.0.74
2) 192.168.0.51
3) 192.168.0.22
Select remote: 1
**************************
sending incremental file list
some_dir/
some_dir/some_other_dir/

sent 128 bytes  received 24 bytes  304.00 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)

**************************
Do you wish to commit to these changes (y/n)? y

**************************
sending incremental file list
some_dir/
some_dir/some_other_dir/

sent 124 bytes  received 24 bytes  296.00 bytes/sec
total size is 0  speedup is 0.00

**************************
done!

```

Now, on the remote machine (192.168.0.74)

``` console
$ ls -l
drwxr-xr-x  3 user wheel 4096 Mar 30 03:27 some_dir
```

# Requirements
- nmap
- awk
- ip

# Setup
## 1. Open ssh port
todo
## 2. Add ssh-keys
todo

# Installation

I recommend creating a directory ~/src and cloning the repository into that.
Then, we create a soft-link in /usr/local/bin which should be part of the PATH
variable, so that `homesync` is available as a command. 

Then, whenever an update is pushed to homesync, it can be updated simply by a
git pull in the src/homesync directory.

``` console
$ if [ ! -d ~/src ]; then mkdir ~/src; fi  && cd ~/src
$ git clone https://github.com/deanpoulos/homesync.git
$ cd homesync
$ chmod +x homesync
$ cd /usr/local/bin
$ sudo ln -sf ~/src/homesync/homesync
```
