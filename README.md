# keepassxc-dmenu
dmenu frontend for keepassxc to copy username, password and notes quickly

## Dependendies
* dmenu
* gnupg
* keepassxc-cli (already installed if you have keepassxc)

## Usage

* Generate a GPG key pair:
```
gpg --full-gen-key
```
and follow the instructions

* Put the password to your database in a file(`pass` here). encrypt it using gpg and delete the original file (nobody can see the contents of encrypted file without the gpg passphrase)
```
gpg -e -r $(whoami) pass # Encrypt pass. create a pass.gpg file
rm pass                  # Delete the original file
```

* Change the `database` variable in the script to point to the keepassxc database and the `passgpg`
variable to point to the pass.gpg file created in above step.

* Download & place the script in `$HOME/bin/` and make the script executable
```
chmod +x keepmenu
```

* Bind it to a key. E.g. if using `xbindkeys` add the following to `~/.xbindkeysrc` to bind it to Ctrl+F1
```
# Path to script
"$HOME/bin/keepmenu"
Control+F1
```
