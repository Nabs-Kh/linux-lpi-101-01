
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

## Session 03 - Homework
1. Create the following directory structure + files using the minimum possible number of commands
for the following stock categories: `Grocery`, `Linen`, `Fruits`, using the below example as a template

```
stock
 |_____ Grocery
        |_____ 2010
        |       |_____ m1
        |       |      |_____ invoice1.txt
        |       |      |_____ invoice2.txt
        |       |      |_____ invoice3.txt
        |       |      |_____ ...
        |       |      |_____ invoice100.txt
        |       |_____ ...
        |       |_____ m12
        |
        |_____ 2011
        |       |_____ m1
        |       |      |_____ invoice1.txt
        |       |      |_____ invoice2.txt
        |       |      |_____ invoice3.txt
        |       |      |_____ ...
        |       |      |_____ invoice100.txt
        |       |_____ ...
        |       |_____ m12
        |
        |_____ ...
        |_____ 2020
                |_____ m1
                |      |_____ invoice1.txt
                |      |_____ invoice2.txt
                |      |_____ invoice3.txt
                |      |_____ ...
                |      |_____ invoice100.txt
                |_____ ...
                |_____ m12
```

2. What is the difference between Hard and Soft links in linux

## Regex
- select all years
- select all Proper Name
- select all words with 3 characters length
- select all words that are between 2 and 5 length
- select all words that are greater than 2
- select all words that are shorter than 5
- select the sequence that match a Capital Letter + many lower case character and end with a number
- select the words (the,this,that,those)


## Grep
grep -l -r hello *
grep -l -r hello students employees salaries.cs

grep -l -r hello */*
grep -l -r hello students/english students/linux  employees/managers employees/hr

grep -l -r hello */*/*
grep -l -r hello students/english/2010 students/english/2011 students/linux/2010 students/linux/2011  ....

/students
	- english
		- 2010
		- 2011
	- linux
		- 2010
		- 2011

/employees
	- managers
		- 2010
		- 2011

	- hr
		- 2010
		- 2011
/salaries.cs


Search for "public" in the current directory and all subdirectories for files ending with "*.cs"
```sh
grep -r "public" **/*
```

## Exercise
```sh
wget ahmadmoussawi.com/users.txt
```

- display all file names that contains the word "hello" or "Hello"
```sh
grep -li "hello" *
```
- display all file names that contains the word "hello" or "Hello" in the current directory and all subdirectories

```sh
grep -lir "hello" .
```
- display all file names that contains the word "hello" or "Hello" in the `/home` directory and all subdirectories

- display all file names that contains the word "hello" or "Hello" that ends with ".html"
```sh
grep -li "hello" *.html
```

- display all file names that contains the word "hello" or "Hello" that ends with ".txt" and starts with capital A

- find all file names with the count, that contains the word "the"
```sh
grep -lc "the" *
```

- in the file users.txt, find all lines that contains "ne" in their name
```sh
grep "ne" users.txt
```

- in the file users.txt, find all lines that not contains "ne" in their names
```sh
grep -v "ne" users.txt
```

- in the file users.txt, find all lines that starts with a word that matches the following rule: Capital Letter, many lower case letter, number

```sh
grep -E -w "[A-Z][a-z]+[0-9]" users.txt
egrep -w "[A-Z][a-z]+[0-9]" users.txt
```

- in the file users.txt, the lines that starts with a Capital Letter

- in the file users.txt, the lines that ends with a voyel.


