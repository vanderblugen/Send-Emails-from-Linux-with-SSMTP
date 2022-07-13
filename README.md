# Send-Emails-from-Linux-with-SSMTP

This is for configuring Linux to be able to send emails.

This information was obtained from [here](https://medium.com/swlh/setting-up-gmail-and-other-email-on-a-raspberry-pi-6f7e3ad3d0e) for my enjoyment and so I don't have to look for this again.  This has been tested on a Raspbery pi and an Ubuntu machine.  Works on both.  I accept no responsibility on if this works or not.

This configuration uses Gmail as the email carrier.  It will work with others, just used gmail in this configuration.  Less secure apps or 2 factor with app passwords needs to be enabled for this configuration to work.


## Install needed apps
```shell
sudo apt-get install ssmtp mailutils -y
```

## Edit ssmtp.conf configuration file
```shell
sudo mv /etc/ssmtp/ssmtp.conf /etc/ssmtp/ssmtp.conf.bak
sudo nano /etc/ssmtp/ssmtp.conf
```


### Paste and update this information into the file and Ctrl+X to exit
```shell
root=GmailEmailAddress@gmail.com
mailhub=smtp.gmail.com:587
hostname=raspberrypi
AuthUser=GmailEmailAddress@gmail.com
AuthPass=TheGmailPassword
FromLineOverride=YES
UseSTARTTLS=YES
```

## Edit revaliases configuration file
```shell
sudo nano /etc/ssmtp/revaliases
```

### Update this information in the file
```shell
root:GmailEmailAddress@gmail.com
postmaster:GmailEmailAddress@gmail.com
```

## Send test email
```shell
echo "Test Email" | mail -s "Test Email" DestinationTestEmail@Address.com
```
