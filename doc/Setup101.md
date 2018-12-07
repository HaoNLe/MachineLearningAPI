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
4. Enter your payment information and apply referral code: `TODO`
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
### Logging in and updating machine
* TODO git pull
* TODO conda env update
* TODO password change

### Jupyter Notebook Server
* TODO

### Shutdown
* TODO

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
