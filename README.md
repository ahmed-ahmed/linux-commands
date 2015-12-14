# linux-commands

Use "man" with any command to display the manual
```sh
  man ls 
```
```sh
whoiam              # who is the current logged in user 
hostname            # what's the current host name 
pwd                 #what's the current directoy 
```
#### files and directories: 

 * ~ = home directory
 * /var  =  holds the files that changes frequently
 * /var/log/syslog*   = these are the logs files

#### directory listing 
```sh
ls
ls -l
ls -l p*      #everything starting with p
ls -l -G      # or --no-group will remove group information 
```
#### file information: 
image attached
```sh  
  -rw-rw-r-- 1 ama29  3 Dec  2 13:59 a
  ```

#### editing and view files 
```sh  
echo "line 1" >> file1.txt      # write to a file 
cat file1.txt                   # view contents of file 
tail file1.txt                  # view the last lines of a file 
less file1.txt                  # view long file content and navigate through pages use "q" to exit file 
```
#### manage files permissions  
```sh  
chmod a+w       #a means all users +w means add write
chmod u+w       #u means owner +w means add write
chmod a-w       #remove write permission from all users 
chown ahmed file1.txt       # change owner of the file 
```

## Combinning commands 
- find command only find files 
- chmod command only change files permissions 
- if you combined both commands you can change the permission of set of files with one line of code 

```sh
find p* -print0 | xargs -0 chmod a+r    # change permission of all files starts with p

            # -print0 format ouput 
            # xargs break the output and execute chmod once per each item of the output 
```




