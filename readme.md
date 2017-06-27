## Local Installation

## Deployment

## Server Setup


Register for an account here
https://www.digitalocean.com/

### Create a droplet
![image](https://user-images.githubusercontent.com/17580530/27603515-4db92654-5b44-11e7-9e43-29093e963e38.png)

### Select Ubuntu 16.04.2 x64
![image](https://user-images.githubusercontent.com/17580530/27603543-657ad4ae-5b44-11e7-9dd0-e4d7d6de8432.png)

### Select server size (5/mo)
![image](https://user-images.githubusercontent.com/17580530/27603553-6df97590-5b44-11e7-9cca-2c9847b2840a.png)
### Select datacenter region *closest to you*
![image](https://user-images.githubusercontent.com/17580530/27603568-796689ae-5b44-11e7-9e2d-960e72f6322f.png)

* **Don't worry about private networking/backups/etc**

* Add SSH key if you have one already. If not, [heres a tutorial](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets) on using them.
* Select how many droplets you want and give each server a name
* Select the server you want to view it's control panel

### Root Login
To login to your server you need two things:
1. Your server's public IP address
2. Your password set up in Digital Ocean OR the private key you installed for that server
	
Once you have those, in terminal you can run:

`$ ssh root@<YOUR_IP_ADDRESS>`

Change or add new passwords wherever you are prompted to with a strong password.

### Create a New User
Root is the Juggernaut of your server and can cause accidental chaos very easily. Create a new user that has less destructive powers that you can use more freely.

If you're currently logged in to your server via root, in terminal run:

`# adduser <USERNAME>`

Enter a good password for your new user and fill out any prompted fields *if you like.*

### Root Privileges
Users who don't have root privileges may be able to use the `sudo` command if they belong to the "sudo" group. This command gives that user temporary administrative access over whatever they want to accomplish. 

By now you should be logged in as `root`; in terminal to add the user you created to the "sudo" group run:

`# usermod -aG sudo <USERNAME>`

### Public Key Authentication
Skip this step if you already have an SSH key on your server.
#### Generate a Key Pair

Open a new terminal window or logout of your server using `logout` and run:

`$ ssh-keygen`

Hit Enter to save the key into the path `(/Users/<YOUR_USER>/.ssh/id_rsa)`

Enter a passphrase if you want to. 
***You will need both the passphrase and the private key to log in to your sever this way***

#### Copy the Public Key to Your Server

##### Option 1
***If you selected an SSH key in Digital Ocean use Option 2***
In terminal run:

`$ ssh-copy-id <USERNAME>@<YOUR_IP_ADDRESS>`

If that command is not found you can use Homebrew to install it then re-run

`brew install ssh-copy-id`

##### Option 2
In terminal run:

`$ cat ~/.ssh/id_rsa.pub`

You should see a long output that ends with something similar to `<YOUR_USER>@<YOUR_MACHINE_NAME>.local`

Select and copy that whole output.

You now need to *Enable Public Key Authentication*

You must add this copied public key to a specific file in your *server user's* home directory.

Log in to your server **as root** and switch to your created user by running:

`# su - <USERNAME>`

You are in your user's home directory.

Make a new directory called `.ssh` and give **only the root user** full permissions by running:

`$ mkdir ~/.ssh`
`$ chmod 700 ~/.ssh`

If you're still within your user's home directory, double check the commands worked by running `ll` in your terminal. You should see a line that looks like:

`drwx------ 2 <USERNAME> <OWNER> 4096 <created_date> .ssh/`

Create and open a new file **inside** of `.ssh` called `authorized_keys`. In terminal run:

`$ nano ~/.ssh/authorized_keys`

Paste the public key you copied when you ran `$ cat ~/.ssh/id_rsa.pub` on your local machine.

	Hit `CTRL-x` to exit
	Hit `y` to save
	Hit `ENTER` to confirm the file name

Now give **only the root user** read and write permission to the `authorized_keys` file by running:

`$ chmod 600 ~/.ssh/authorized_keys`

Exit as **root** by running:

`$ exit`

Now you can use SSH to log in as your new user.