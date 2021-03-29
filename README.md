# Todo

- [ ] Add config file
- [ ] Add man page

# Description

A tool for syncing specified directory structures between machines 
on the same network.

# Usage

``` console
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

# Installation

git clone ...
