- [Linux](#linux)
  - [Getting started](#getting-started)
- [File Management](#file-management)
  - [`cd, ls`](#cd-ls)
  - [content](#content)
  - [`vim`](#vim)
  - [`rm, mv, cp`](#rm-mv-cp)
- [Other commands](#other-commands)
  - [Resources (CPU, GPU, Network, etc.)](#resources-cpu-gpu-network-etc)
  - [Executeable](#executeable)
  - [misc](#misc)

## Linux

### Getting started

- Buy a Mac
- Install Linux OS (Ubuntu, CentOS, RHEL, etc.)
- Install WSL in Windows

## File Management

### `cd, ls`

```bash
cd FOLDER_NAME
cd ..


ls
ls -l       # long format
ls -h       # human-readable format of size (2.1M, 8.5G)
ls -t       # sort with last-updated time
ls -r       # reverse order

ls -l -t    # display long format, sort with last-updated
ls -lt      # same as the above
ls -lrt     # display long format, sort with reverse last-updated time
            # The lower file, the newer file

# for example
ls -lrth
    # total 48
    # drwxr-xr-x  5 smalldragon  staff   160B  3 16  2021 __pycache__
    # -rw-r--r--  1 smalldragon  staff   1.6K  3 16  2021 meter.py
    # -rw-r--r--  1 smalldragon  staff   3.5K  3 18  2021 model.py
    # drwxr-xr-x  4 smalldragon  staff   128B  3 20  2021 ckpts
    # -rw-r--r--  1 smalldragon  staff    11K  3 24  2021 dataset.py
    # -rw-r--r--  1 smalldragon  staff   3.4K  4 16  2021 train.py
```

### content

```bash
echo "goodjob"          # display text on command line

cat FILE.txt            # show file content

head FILE.txt           # show head n lines (default: 10)
head -n 5 FILE.txt      # show head 5 lines
tail FILE.txt           # show tail n lines (default: 10)
tail -n 5 FILE.txt      # show tail 5 lines

wc cube.py              # stand for "word count"
# count lines/words/characters of this file
    # 22      84     503 cube.py

wc -l cube.py           # count lines
    #   22 cube.py
wc -w cube.py           # count words
    #   84 cube.py
wc -c cube.py           # count character
    #  503 cube.py
```

### `vim`
```bash
vim             # start vim program
vim a.txt       # start vim with a new file named "a.txt"
```

Vim is a complex command-line editor for newbie.  
The biggest problem is how to switch between view/edit/command modes.  
宏任 had a good cheatsheet I remember.  

#### Inside vim
- Type **"i"** (or some other keys) to exit **view** mode and enter **edit** mode
- Type **"Esc"** to exit **edit** mode and enter **view** mode
- Type **":"** to exit **view** mode and enter **command** mode

#### Useful command in "command mode"
| command       | description                              |
|---------------|------------------------------------------|
| w             | write(save) changes into file            |
| q             | quit (if there is no changes)            |
| wq            | save file and quit it                    |
| !             | force                                    |
| w!            | force save                               |
| q!            | fore quit (without save current changes) |
| number        | jump to lines                            |
| set number/nu | show line numbers                        |
| undo          | undo                                     |
| redo          | redo                                     |

#### Useful shortcut key in "view mode"
         
| command | description               |
|---------|---------------------------|
| /       | start search some pattern |
| n       | next search result        |
| Shift+4 | jump line end             |
| Shift+6 | jump to line start        |


### `rm, mv, cp`

#### rm

```bash
ls

rm NAME.txt
rm N1.txt N2.txt

rm DIRECTORY    # wrong
# rm: DIRECTORY: is a directory

rm -r DIRECTORY

rm -f NAME.txt  # force delete files
rm -rf DIR      # force delete folders
```
```bash
mv THIS/NAME.txt THAT/NAME.txt  # move from THIS folder to THAT folder
mv NAME.txt NAME2.txt           # rename from NAME to NAME2
mv NAME.txt NAME.py             # rename extension name
mv THAT/NAME.txt THIS.py        # move file from THAT to current directory and rename it
```

```bash
cp THIS/NAME.txt THAT/NAME.txt  # copy from THIS folder to THAT folder
cp NAME.txt ..                  # copy NAME.txt to parent directory
cp NAME.txt NAME.py             # copy a file named NAME.py

cp DIRECTORY ..                 # wrong
# cp: out is a directory (not copied).
cp -r DIRECTORY ..              copy the whole folder to parent directory
```

## Other commands

### Resources (CPU, GPU, Network, etc.)
```bash
htop                # overview of system
nvidia-smi          # nvidia offical monitor
nvtop               # htop-like GPU monitor
ifconfig            # show the network info

ping xxx.com        # try to reach the website
# PING google.com (142.251.42.238): 56 data bytes
# 64 bytes from 142.251.42.238: icmp_seq=0 ttl=116 time=23.456 ms
# 64 bytes from 142.251.42.238: icmp_seq=1 ttl=116 time=11.584 ms
# 64 bytes from 142.251.42.238: icmp_seq=2 ttl=116 time=8.600 ms
# 64 bytes from 142.251.42.238: icmp_seq=3 ttl=116 time=7.467 ms

# You can know the real ip address
```

### Executeable
```bash
which EXECUTABLE        # the real path of this executable file
whereis EXECUTABLE      # list all of the executable located

python                  # run the executable
/PATH/TO/python         # directly run the executable

EXECUTABLE -a -b        # single-char flag
EXECUTABLE -a 3 -b "go" # single-char flag
EXECUTABLE --apple --banana # word flag
EXECUTABLE --apple 10 --banana "../hello.go" \ # escape line
    --cat "cute" --data "../img/" # word flag
```

### misc

```bash
ln /FROM/a.run /TO/b.run    # make a link
ln -s/FROM/a.run /TO/b.run  # make a soft link

sh SOME_NAME.sh         # run a shell script, e.g. get docker

wget, curl              # networking
```