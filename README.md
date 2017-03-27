# WinSCP Custom Commands

A list of useful commands for daily work with WinSCP.

## Installation

If you use an .ini file to store your configuration, simply append the content of [WinSCP.ini](WinSCP.ini) to your .ini file.

If you use the windows registry you have to add every command manually or you switch to .ini configuration, add the config and then switch back to registry storage.

If you have pre-existing commands, merge them manually. The WinSCP default ones are included.
 
_Hint: To switch to .ini file configuration go to Options -> Preferences -> Storage_ 
  
## List of commands 

### BasicAuth (.htaccess)
Creates a .htaccess and a corresponding .htpasswd.
You're prompted for user and password.

```
printf "AuthUserFile !/.htpasswd \nAuthType Basic\nAuthName 'Password protected'\nrequire valid-user" > !/.htaccess && htpasswd -cmb  !/.htpasswd !?&User:?! !?&Password:?! 2>&1 
```

### BasicAuth add
Adds a new user to an existing .htpasswd file.
You're prompted for user and password.

```
htpasswd -mb  !/.htpasswd !?&User:?! !?&Password:?! 2>&1
```
### info.php
Creates a file info.php with the phpinfo() function
```
printf "<?php phpinfo(); ?>" > ./info.php
```

### Folder size
Shows the size of the current folder in the terminal.

_Check custom command option Show results in terminal._
```
du -sh $PWD
```

### Chmod
Chmod selected files and folders recursively (!)
You're prompted for the permissions in octal code.

_Check custom command options Apply to directories_ 
```
chmod -R "!?Permissions:?0755!" !&
```

### Chown
Chown selected files and folders recursively (!)
You're prompted for user and group.

_Check custom command options Apply to directories_ 

```
chown -R "!?New owner:?www-data!":"!?New group:?www-data!" !&
```

### Delete
Executes a rm -rf recursively (!). You're asked for confirmation.
This is useful for a quick delete on the server side.

```
test "!?Do you really want to delete ?no!" == "yes" && rm -rf ./!&
```


Checkout https://winscp.net/eng/docs/custom_commands for additional commands and syntax


