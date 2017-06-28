## Local Installation


## SCP Deployment

#### Prerequisites
For this process, you will need to have:
	
	• A Ubuntu 16.04 server
	• A non `root` user
	• Your public IP address

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
104.236.209.24

`$ scp humans.txt <USERNAME>@<YOUR_IP_ADDRESS>:/var/www/html`

If successful, you should see the output:
`humans.txt                                    100% 1584     1.6KB/s   00:00 `

Now, you can login to your server using your `sudo` user and find that the file was properly added by running:

`$ ls /var/www/html`

Make sure you are able to locate the `humans.txt` file and you have completed basic SCP deployment.

## Server Setup