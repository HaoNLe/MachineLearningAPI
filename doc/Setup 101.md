**Making a directory**
`
mkdir mydir                 # Creates a new directory
mkdir -m a=rwx mydir        # Creates a new directory and set permissions so all users may read, write, and execute the contents.
mkdir test1 test2 test3     # Creates multiple directories
mkdir -p /home/test/test1/test2/test3/test4
                            # Creates multiple subdirectory levels at once
`

**Moving files/directories**
`
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
`

**Unzipping a zipped file**
`
unzip training_set.zip      # Unzips training_set in its current directory
`
You'll want to move the zipped file into its own folder before unzipping like so:
`
mv training_set.zip training_set/training_set.zip
cd training_set
unzip training_set.zip
`
