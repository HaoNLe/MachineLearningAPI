## Paperspace Setup
### Creating the Machine
1. Create paperspace account: [here - signup](https://www.paperspace.com/account/signup)
2. After logging in go to Core -> Computer -> Machines or click [here - machines](https://www.paperspace.com/console/machines)
3. Click "New Machine" and configure like so:
   * Choose West Coast for region
   * Under Public Templates choose Fast.ai
   * Select hourly GPU+
   * Select 50GB for storage (5$/mo)
      * note that you pay for storage as soon as you start the machine up so don't mess up!
   * Turn off Auto Snapshot
   * Turn on Public IP (3$/mo)
4. Enter your payment information and apply referral code: https://www.paperspace.com/&R=P4LLNPI
   * Payment info is required even with a code
5. Click "Create Your Paperspace"
6. You'll receive an email with a temporary password once your machine is ready
```
Hi there,

Congratulations! Your new Paperspace Linux machine has been created, and is ready when you are!

Your temporary sign-in password for machine New Machine 1 is: *************

You can ssh into your new machine with the following command:ssh paperspace@##.###.###.###

Happy computing!
- The Paperspace Team
```

Below section modified from https://github.com/reshamas/fastai_deeplearn_part1/edit/master/tools/paperspace.md

## :red_circle: Part III:  Updating repo contents
* :key:  this step is important as having updated content and libraries can bypass errors

### Step 1:  go to directory
<kbd> cd fastai </kbd>  
```
(fastai) paperspace@psnqh1ltz:~$ cd fastai
(fastai) paperspace@psnqh1ltz:~/fastai$ pwd
/home/paperspace/fastai
(fastai) paperspace@psnqh1ltz:~/fastai$
```

### Step 2:  update repo 
<kbd> git pull </kbd>  
- from time to time, you should pull the latest `fastai` repo from GitHub
```bash
(fastai) paperspace@psnqh1ltz:~/fastai$ git pull
Already up-to-date.
```

### Step 3:  update Python / Anaconda libraries
<kbd> conda env update </kbd>  
- do this from time to time (every few weeks)

### Step 4 (optional): Update password and apply root password
<kbd>passwd</kbd> and <kbd>sudo passwd</kbd>
- Current password = temp from Paperspace email
- Root (sudo) currently has no password... we should set that too.
```bash
(fastai) paperspace@psjs5366a:~$ passwd
Changing password for paperspace.
(current) UNIX password:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
(fastai) paperspace@psjs5366a:~$ sudo passwd
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
(fastai) paperspace@psjs5366a:~$
```

---
## Part IV:  Paperspace & Jupyter Notebook
### Step 1:  `cd` into fastai directory
- make sure you are here:  `/home/paperspace/fastai`
```bash
(fastai) paperspace@psgyqmt1m:~/fastai$ pwd
/home/paperspace/fastai
(fastai) paperspace@psgyqmt1m:~/fastai$
```

### Step 1.5: Fix Jupyter Notebook config file
<kbd> jupyter notebook --generate-config </kbd>
- The config file was previously set up by default to allow remote access, but updated jupyter notebook breaks.
```bash
(fastai) paperspace@psgyqmt1m:~/fastai$ jupyter notebook --generate-config
Overwrite /home/paperspace/.jupyter/jupyter_notebook_config.py with default config? [y/N]
```

### Step 2:  Launch Jupyter Notebook (now with more config!)
<kbd> jupyter notebook --no-browser --port=8889 --NotebookApp.allow_remote_access=True</kbd>
- the config settings can be written permanently into /home/paperspace/.jupyter/jupyter_notebook_config.py.
- The reason to change port=8889 will be clear in a minute.

```
(fastai) paperspace@psgyqmt1m:~/fastai$ jupyter notebook --no-browser --port=8889 --NotebookApp.allow_remote_access=True
[I 20:37:41.604 NotebookApp] Serving notebooks from local directory: /home/paperspace/.jupyter
[I 20:37:41.605 NotebookApp] The Jupyter Notebook is running at:
[I 20:37:41.605 NotebookApp] http://localhost:8889/?token=a7a724c1ba8d4c91132834c2d076298f517002227d4e8a72
[I 20:37:41.605 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 20:37:41.605 NotebookApp]

    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8889/?token=a7a724c1ba8d4c91132834c2d076298f517002227d4e8a72
```

### Step 2.5:  SSH into machine and redirect <i>local</i> localhost to machine localhost
- open a terminal or cmd window on your <b>local</b> machine 
- <kbd>ssh -N -L localhost:8888:localhost:8889 paperspace@your.public.ip.here</kbd>

```
C:\Users\Me>ssh -N -L localhost:8888:localhost:8889 paperspace@184.###.###.###
The authenticity of host '184.###.###.### (184.###.###.###)' can't be established.
ECDSA key fingerprint is SHA256:bWbbhUD/7KFh+AM5CtmcSR8Z+n4rNp4p3D+V5q7P8Sw.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '184.###.###.###' (ECDSA) to the list of known hosts.
paperspace@184.###.###.###'s password:

```
- keep this cmd window open. It appears to hang after enter on password, but all good.
- this was sourced from https://hsaghir.github.io/data_science/jupyter-notebook-on-a-remote-machine-linux/
- For a more permanent solution, see **Optional** section below

### Step 3:  Get Notebook url
- copy jupyter notebook URL <kbd>http://localhost:8889/?token=a7a724c1ba8d4c91132834c2d076298f517002227d4e8a72</kbd>
- paste url into your local browser (example:  Chrome, Firefox, Opera, etc) and change port from 888**9** to 888**8**
- :boom: Hooray, it works! :smiley:   
- alternately, bookmark <kbd>localhost:8888</kbd> and use the token <kbd>a7a724c1ba8d4c91132834c2d076298f517002227d4e8a72</kbd> to log in.
    - Note: the token changes each time you restart jupyter notebook on the Paperspace machine

---
## Part V:  Workflow
I opened the [Lesson 1 notebook](https://github.com/fastai/fastai/blob/master/courses/dl1/lesson1.ipynb), made a copy with the name `tmp-reshama-lesson1.ipynb`  

http://184.###.###.###:8888/notebooks/courses/dl1/lesson1.ipynb


## :red_circle: Part VI:  Shutting down Notebook & Machine
### :red_circle: Remember to shut the notebook down and STOP Instance! :moneybag: :red_circle:

- Paperspace has an option where you can choose to automatically shut down your machine at: 1 hr, 8 hrs, 1 day, 1 week
- I chose the `8 hrs` option
- :key: Note that the auto shut down works only for the browser console. **Paperspace will not auto shut down your server if you SSH to it.**
- [How do I use Auto-Shutdown on my Linux machine when connecting through SSH?](https://paperspace.zendesk.com/hc/en-us/articles/115002807447-How-do-I-use-Auto-Shutdown-on-my-Linux-machine-when-connecting-through-SSH-)
<img src="../images/paperspace.png" align="center"  height="500" width="750" >   

---
## Unix Commands
You'll be needing these in order to use your own datasets.
**Making a directory**
```
mkdir mydir                 # Creates a new directory
mkdir -m a=rwx mydir        # Creates a new directory and set permissions so all users may read, write, and execute the contents.
mkdir test1 test2 test3     # Creates multiple directories
mkdir -p /home/test/test1/test2/test3/test4
                            # Creates multiple subdirectory levels at once
```

**Moving files/directories**
```
mv myfile mynewfilename     # renames 'myfile' to 'mynewfilename'.
mv myfile ~/myfile          # moves 'myfile' from the current directory to user's home directory.
                            # the notation '~' refers to the user's "home" (login) directory
mv myfile subdir/myfile     # moves 'myfile' to 'subdir/myfile' relative to the current directory.
mv myfile subdir            # same as the previous command, filename is implied to be the same.
mv myfile subdir/myfile2    # moves 'myfile' to 'subdir' named  'myfile2'.
mv be.03 /mnt/bkup/bes      # copies 'be.03' to the mounted volume 'bkup' the 'bes' directory, 
                            # then 'be.03' is removed.
mv afile another /home/yourdir/yourfile mydir 
                            # moves multiple files to directory 'mydir'.
mv /var/log/*z ~/logs       # takes longer than expected if '/var' is on a different file system, 
                            # as it frequently is, since files will be copied & deleted
                            # be careful when using globbable file name patterns containing
                            # the characters ?*[ to ensure that the arguments passed to 'mv'
                            # include a list of non-directories and a terminating directory

man mv                      # displays the complete UNIX manual page for the 'mv' command.
```

**Unzipping a zipped file**
```
unzip training_set.zip      # Unzips training_set in its current directory
```
You'll want to move the zipped file into its own folder before unzipping like so:
```
mv training_set.zip training_set/training_set.zip
cd training_set
unzip training_set.zip
```
