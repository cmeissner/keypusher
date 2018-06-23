# keypusher

keypusher - install a known public keys in remote machines authorized_keys file

```keypusher [ hostname | username | regex ]```

## Description

keypusher  will  help you to distribute ssh pubkeys of your employees and partners to many systems. You can redistribute all keys to all machines or you can
send keys only to single systems or systems which matches to a given regex. keypusher is completly written in bash. So feel free to improve it or to develop
new features.

## Files

There  are some files and directories which hold information of public keys, posix users and mappings. There is also a central configuration file which will
keep some basic settings.

```/etc/keypusher/keypusher.conf``` - basic configuration file

```/etc/keypusher/userkeys``` - Here you save all your user public keys. The naming format is <name>.pub. The <name> part is used to reference to a single key  in
other configuration files.

```/etc/keypusher/users```  -  Here  you  can place text files which holds the default mapping of userkeys to a posix user. For each posix user you have to save a
file with user name a file name.

## Examples

If you will configre Bob's public key in keypusher you have to place his public key in ```/etc/keypusher/userkeys/bob.pub``` From now it can be  referenced  by  using
"bob" in all possible config files.

On all you system should exist the keys of backup and ceo in authorized_keys file of user root. So you have to write a FIle /etc/keypusher/users/root with
the following content:

		backup
		ceo

In ```/etc/keypusher/userkeys``` have to stored the public keys ```backup.pub``` and ```ceo.pub```.

## See also

keypusher.conf(5), host.map(5), user.map(5), ssh-copy-id(1), sshd(8)
