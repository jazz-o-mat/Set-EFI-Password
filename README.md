Set EFI Password
----------------

This script allows the user to set, change and remove an EFI password from computer(s).

I forked the version from https://github.com/franton/Set-EFI-Password.git. I changed it for standalone use and fixed it for 10.10 and 10.11. (credits go to Richard Purves) 

It uses setregproptool straight from the Recovery partition rather than having to continually package the correct version and deploy it to the computer.
You can wrap the script into a package and deloy this via munki etc. 

Instructions
------------
- When calling the script you must specify the following information:

Parameter 1: Operating Mode - This tells the script whether to set, change or remove a password.
Acceptable inputs are "initial", "change" or "remove".

Parameter 2: New Password - This is the new password you wish to give the system (use "" for empty passwords)

Parameter 3: Old Password - Required for password changes and removal (use "" for empty passwords)

Parameter 4: Security Mode - This is the mode that the EFI password will operate in.
(This option is required for "initial" and "change" operating modes)
Acceptable inputs are "full" and "command".

"full" will apply the EFI password to the entire computer. This will prevent ANY booting without a valid password!
"command" will apply the EFI password to the boot picker. This will allow booting to the selected startup disk but nothing else!

Be careful with this! This password is stored in a separate secure chip on Apple's computers past 2010 and if you forget, it's a trip to the Apple Store to get it reset.
