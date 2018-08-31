---
layout: post
title: "How To Add 2FA (Two Factor Authentication) in the VPS SSH"
description: "Guide to setup 2FA in any VPS SSH login"
category: articles
tags: [linux, 2fa, SSH]
comments: false
---

Sometimes you may need to ensure extra security for your VPS. I needed to set up many VPS but I was thinking what should be the best thing to do for making sure that they are not vulnerable to attacks. So, I wanted to add two factor authentication on these VPS. So, I started looking for articles and found one in stack overflow which directed me to what I wanted to do.

I am just documenting this process for me and also for people who may need to do this in future. I was using Ubuntu 16.04, but I guess the procedures are similar in Ubuntu 18.04 too. Please, let me know if the process is different in the latest version of Ubuntu.  

## What you will need

{% highlight bullet %}
> Ubuntu 16.04;

> A non-root user;

> You can create a non root user by having a new username and giving the username sudo permit.

{% endhighlight %}

## 2FA SSH IN TERMINAL Step: 1, Download the files

First, download the google two factor authentication by:

```
$ sudo apt-get install libpam-google-authenticator
```

```
$ google-authenticator

```

## 2FA SSH IN TERMINAL Step: 2, time-skew and configuration

After downloading the google authenticator you need to prompt Y for the next four steps, where first it will ask for time based tokens. If you select N, then it will be only usable for once.

```
Do you want authentication tokens to be time-based (y/n) y

```

Here it is asking your permission to update your directory.

```
Do you want me to update your "/home/user/.google_authenticator" file (y/n) y

```
The next prompt provides all the information itself:

```
Do you want to disallow multiple uses of the same authentication
token? This restricts you to one login about every 30s, but it increases
your chances to notice or even prevent man-in-the-middle attacks (y/n) y
```

Then it will give you another prompt, here you can return n but I sticked with y.

```
By default, tokens are good for 30 seconds and in order to compensate for
possible time-skew between the client and the server, we allow an extra
token before and after the current time. If you experience problems with poor
time synchronization, you can increase the window from its default
size of 1:30min to about 4min. Do you want to do so (y/n) y
```

 If you want to change this time-skew later, you can rerun this configuration step and the follow the same process but this time select n instead of y.

## 2FA SSH IN TERMINAL Step: 3, Saving the QR code

After doing all this, you will see QR code shown in your terminal along with other credentials. Copy and Save them somewhere safe.

You can keep them safe in your local machine or you can use something like KeePass if you have lot of data.
I will show in future, how can you create a database of this information and store them securely.

## 2FA SSH IN TERMINAL Step: 4, Enabling Google authenticator in SSH

In this step you will enable 2FA. To enable 2FA when SSH login go to this file, you must set `PubkeyAuthentication` to `no` and `PasswordAuthentication` to `yes`

If its already set by default then you can go to the next step which is editing sshd file.

```
sudo vim /etc/pam.d/sshd
```

Add this following line in the beginning

```
auth required pam_google_authenticator.so

```
After this, you can go to the sshd configuration file by
```
cat /etc/ssh/sshd_config
```
or do the following, if you have to edit it. Press i to enter insert mode and esc then :wq if you edit, :q! if you do not want your edit to be saved and want to quit, if you did not do any change do this :q to quite.
```
sudo vim /etc/ssh/sshd_config
```
Alternatively use nano editor
```
sudo nano /etc/ssh/sshd_config
```
and look for `ChallengeResponseAuthentication` You must set it to yes, if the line is commented then uncomment the line or add it, if it is not there.

This line of configuration should look like this:
```
ChallengeResponseAuthentication yes
```
## Final step: Step 5

Finally, you just need to restart the sshd by:

```
$ sudo systemctl restart sshd
```

Now, your 2FA for VPS should be ready to be used. Enjoy your server.
