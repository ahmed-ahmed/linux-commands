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
chmod a+w                       #a means all users +w means add write
chmod u+w                       #u means owner +w means add write
chmod a-w                       #remove write permission from all users 
chown ahmed file1.txt           # change owner of the file 
```

## Combinning commands 
- find command only find files 
- chmod command only change files permissions 
- if you combined both commands you can change the permission of set of files with one line of code 

```sh
# change permission of all files starts with p
# -print0           format ouput 
#-type f            select only files
# xargs             break the output and execute chmod once per each item of the output 

find p* -print0 | xargs -0 chmod a+r    

#unzip all the logs             
find /var/log/syslog*.gz -type f -print0 | xargs -0 sudo gunzip 
```

#### grep 
looks for mathing lines in the command inputs 
```sh
# -c returns the count 
ifconfig | grep -c "inet6 addr:"            # return no of ip address
ifconfig | grep "inet6 addr:"               # return ip addresses
```

#### head 
return the firsr -n lines 
```sh
ifconfig | grep "inet6 addr:"               # return ip addresses | head -n 3 # retrun the first 3 ips
```
#### cut  
split the input into words 
```sh
ifconfig | grep "inet" | cut -d ":" -f 2            # split by ":" and return the second item
```

# Scripting Commands 
```sh 
# speciying the scripting language (BASH shel) 
#!/bin/bash
# get rge ip address 
address = $(ifconfig | grep "inet" | cut -d ":" -f 2 | cut -d " " -f 1 | head -n 1) 
# print it 
echo $address
# print to file 
echo $address >> ~/ip.txt
```
you need to make sure to make the file executable 

```sh 
chmod u+x script.sh         # make it execuatable
./script.sh                 #run it
```

# Sceduale Tasks (CRON) 
```sh 
crontab -e
```


