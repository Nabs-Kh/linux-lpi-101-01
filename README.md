
Log in as root: `sudo su`

root directory: `/`
root user: the user named root (the batal 💪🏻)
home directory: the home directory for each user, `/home/<username>` and `/root` for root user



## Session 2
==========

`/` the root file system
two types of `path`

 ### absolute path
  - `/`
  - `/home/ahmad`
  - `/var/log/apache.log`
  - `/Users/ahmad/Documents/MyResume.pdf`

 ### relative path
  - `games`
  - `games/gta2`
  - `../pictures`
  - `../../games/gta2`



```sh
pwd = /
cd videos/YouTube

pwd = /videos
cd ../pictures

pwd = /pictures/promotions/2016/Q1 target= /pictures/summer
cd ../../../summer

 /
 |--- games
 |--- documents
 |--- videos
 |------ YouTube
 |------ Family
 |--- pictures
 |------ summer
 |------ winter
 |------ promotions
 |--------- 2016
 |------------ Q1
 |------------ Q2
 |--------- 2017
 |------------ Q1
 |------------ Q2
 |--------- 2018
 |------------ Q1
 |------------ Q2

 ```

### Creating Directories

```sh
mkdir <path of the directory>

pwd = /home/ahmad
mkdir games
mkdir ../games
```

`/home/ahmad/` + `games` = `/home/ahmad/games`
`/home/ahmad/` + `../games` = `/home/ahmad/../games` = `/home/games`

### Removing Directories
```sh
rmdir <path of the directory>

pwd = /home/ahmad
rmdir games
rmdir /
```

### Removing Directories (Preferred method)
```sh
rm -r path/to/directory # -r means recursively
rm -rf path/to/directory # -rf means recursively and force
```


### Quick Lab

Create the following directory structure in one command

```
invoices
|____ 2016
        |___ Q1
        |___ Q2
        |___ Q3
|____ 2017
        |___ Q1
        |___ Q2
|____ 2018
        |___ Q1
        |___ Q2
|____ 2019
        |___ Q1
```


## Directory listing

```sh
ls <path of the directory?> default to pwd
```

- -a to show hidden files

- -l long listing

- -h human readable


### Permissions

check this link [https://chmod-calculator.com/](Linux Permissions Calculator)

![Linux Permissions](linux-permissions.png)

```sh
   user     group       other
-  ---       ---         ---
d  r w x    r w x
-  - - -    - - -
```

```
d rwx      rw-   ---
```

## Creating directory recursively

I use the `-p` flag to create a directory recursively

```sh
mkdir -p products/computers/2010
```

## Remove directory recursively

I use the command `rm` with the flags `-r` and `-f`

```sh
rm -rf products
```
-r : recursive

-f : force

## Path expansions

We use the `{}` to informs the shell that we need to expand the path

For example the following command create the following path

```sh
mkdir -p products/{computers,mobiles}/{2010,2011}/{m1,m2,m3,m4,m5,m6,m7,m8,m9,m10,m11,m12}
```
```
products
        computers
                2010
                        m1
                        m2
                        ...
                        m12
                2011
                        m1
                        m2
                        ...
                        m12
        mobiles
                2010
                        m1
                        m2
                        ...
                        m12
                2011
                        m1
                        m2
                        ...
                        m12
```

The following are equivalent

```sh
mkdir -p products/{computers,mobiles}
mkdir -p products/computers
mkdir -p products/mobiles
```


## Change server hostname

the hostname is stored under `/etc/hostname`

to change it
1 - first option

```sh
echo "newname" > /etc/hostname
```

> *Note:** make sure you are logged as root user

2 - Second option
using the Network Manager Text User Interface (NMTUI)
```sh
nmtui
```
then select change host name option

then reboot the server

### IO Redirection
We use the `>` operator to redirect the output to a device/file

```sh
echo "hello" > filename
```

```sh
ls -lah > mydirectory # print the structure to the file
```

We use the `>>` operator to append content.

### Creating files

```sh
touch filename # create an empty file
```