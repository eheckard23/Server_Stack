#### This codebase is to go over the entire [step-by-step process](https://github.com/eheckard23/Server_Stack/blob/master/setup.md) of setting up a remote Ubuntu 16.04 server securely with Linux, Nginx, MariaDB, and PHP. Once that is complete, the [SCP Deployment](#scp-deployment) section covers how to transfer basic files from your local machine to your remote server.

## Local Installation
## Server Setup
[This document](https://github.com/eheckard23/Server_Stack/blob/master/setup.md) goes through the entire process of setting up an Ubuntu 16.04 with a full LEMP stack and HTTPS configuration.

## SCP Deployment

#### Prerequisites
For this process, you will need to have:
	
	• A Ubuntu 16.04 server
	• A non `root` user
	• Your public IP address
	
If you don't have any of these things, follow the [server setup guide](https://github.com/eheckard23/Server_Stack/blob/master/setup.md) on where to start.

* Find and open the file `humans.txt` within this repository.
* In the top right section, click "Raw" for this file
* Hit `CMD-s` to save this file somewhere on your local machine.

In terminal, navigate to the exact folder where you just saved your `humans.txt` file and make sure all the contents are there by running:

`$ nano humans.txt`

**If you are not inside of the exact folder the file is saved, be sure to include the entire path needed to open the humans.txt file.**

You should be able to see the contents:

```text
/* TEAM */
        Chef:Juanjo Bernabeu
        Contact: hello [at] humanstxt.org
        Twitter: @juanjobernabeu
        From:Barcelona, Catalonia, Spain

        UI developer: Maria Macias
        Twitter: @maria_ux
        From:Barcelona, Catalonia, Spain

        One eyed illustrator: Carlos Mañas
        Twitter: @oneeyedman
        From:Madrid, Spain

        Standard Man: Abel Cabans
        Twitter: @abelcabans
        From:Barcelona, Catalonia, Spain
        
        ...
```
If you're file is good to go then you can use SCP to deploy this file to your remote server. To do so, in terminal run:


`$ scp humans.txt <USERNAME>@<YOUR_IP_ADDRESS>:/var/www/html`

If successful, you should see the output:
`humans.txt                                    100% 1584     1.6KB/s   00:00 `

Now, you can login to your server using your `sudo` user and find that the file was properly added by running:

`$ ls /var/www/html`

Make sure you are able to locate the `humans.txt` file and you have completed basic SCP deployment.