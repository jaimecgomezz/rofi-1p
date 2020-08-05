# rofi-1p

`rofi-1p` is a [1password](https://1password.com/) integration with [rofi](https://github.com/davatorium/rofi). Its power resides on the ability to scan through all your items no matter the type, allowing you to access not only your `username` and `password` for every account, but your `notes`, `identities`, etc.

Inspired by [rofi-1pass](https://github.com/Mange/rofi-lpass) :)



## Features

### Available

- Secure login (via [pinentry](https://www.gnupg.org/related_software/pinentry/index.html))
- Distinct `categories` support:
  - Logins
  - Secure notes
  - Credit cards
  - Identities
  - Passwords
- Scheduled deauthorization process (via [at](http://manpages.org/at)) as seen in the web integration.



### Upcoming

-  `2FA` within `rofi-1p`
- Open item `url`





## Notes

- The scheduled deauthorization process is for the sake of security, so even disabling this feature the [op](https://support.1password.com/command-line-getting-started/) utility revokes your access every 30 minutes.





## Installation

Currently there’s no package available, so a manual installation is required.

### Requirements

- [pinentry](https://www.gnupg.org/related_software/pinentry/index.html), [at](http://manpages.org/at), [jq](https://stedolan.github.io/jq/), [xclip](http://manpages.org/xclip), [op](https://support.1password.com/command-line-getting-started/)

  

1. Install and `login` to your [1password](https://1password.com/) account following the steps described in their page: [Getting started](https://support.1password.com/command-line-getting-started/)

2. Verify you have a `~/.op` folder with a `config` file like these:

   ```sh
   # ~/.op/config
   {
           "latest_signin": "my",
           "device": "XXXXXXXXXXXXXXXXXXXXX",
           "accounts": [
                   {
                           "shorthand": "my",
                           "url": "https://my.1password.com",
                           "email": "an@email.com",
                           "accountKey": "XX-XXXXXX-XXXXXX-XXXXX-XXXXX-XXXXX-XXXXX",
                           "userUUID": "XXXXXXXXXXXXXXXXXXXXXXXXXX"
                   }
           ]
   }
   ```

3. Download the source code

   ```sh
   git clone https://github.com/jaimecgomezz/rofi-1p.git
   ```

4. Access the `rofi-1p` folder

   ```sh
   cd rofi-1p
   ```

5. `Symlink` the `rofi-1p` script to some place accessible by your `PATH` variable

   ```sh
   # Assuming you download the rofi-1p source code in your root folder: ~/
   
   # Available to your account
   sudo ln -s ~/rofi-op/rofi-1p /usr/local/bin
   
   # Available to every account on your computer
   sudo ln -s ~/rofi-op/rofi-1p /usr/bin
   
   # Adding the folder path to your PATH variable
   export $PATH="$PATH:~/rofi-1p"
   ```

6. Run [rofi](https://github.com/davatorium/rofi) with `rofi-1p` as a `modi`

   ```sh
   rofi -modi 1P:rofi-1p -show 1P
   ```





## Mods

### Disabling the scheduled deauthorization

```sh
# Comment the following lines:

# DEATHORIZATION-PROCESS

# prevent_previous_timeouts
# set_auth_timeout
```





## Contributing

Every `PR` is welcomed:)





## License

Code released under the MIT license.

