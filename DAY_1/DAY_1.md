# Module 1
## Day 1— Linux Fundamentals & Shell Navigation
### Exercise
#### Question no 1:
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~$ mkdir -p ~/Module_1/DAY_1/EX_1/project/{src/{rtl,tb,include},docs,scripts,build}
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~$ tree ~/Module_1
/home/zaki/Module_1
└── DAY_1
    └── EX_1
        └── project
            ├── build
            ├── docs
            ├── scripts
            └── src
                ├── include
                ├── rtl
                └── tb

11 directories, 0 files


#### Question no 2:
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~$ cd ~/Module_1/DAY_1
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1$ mkdir EX_2
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1$ cd ~/Module_1/DAY_1/EX_2
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1/EX_2$ wget https://riscv.org/wp-content/uploads/2017/05/riscv-spec-v2.2.pdf

zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1/EX_2$ ls -lh riscv-spec-v2.2.pdf
- output:

-rw-rw-r-- 1 zaki zaki 193K May 10 02:12 riscv-spec-v2.2.pdf
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1/EX_2$ file riscv-spec-v2.2.pdf
- output:

riscv-spec-v2.2.pdf: HTML document, ASCII text, with very long lines (64956), with CRLF, LF line terminators


#### Question no 3:
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1$ mkdir EX_3
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1$ cd ~/Module_1/DAY_1/EX_3

- to generate the file of 100 random nos
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1/EX_3$ for i in {1..100}; do echo $RANDOM >> random_data.txt; done
- to find unique, sort them, and place them in new file which are top 10 most frequent

zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1/EX_3$ sort random_data.txt | uniq -c | sort -nr | head -n 10 > top_frequent.txt
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1/EX_3$ cat top_frequent.txt
- output:
      1 9875
      1 9592
      1 9481
      1 940
      1 8716
      1 8639
      1 8519
      1 8254
      1 7925
      1 7559

#### Question no 4:
zaki@zaki-HP-Envy-x360-2-in-1-Laptop-14-es1xxx:~/Module_1/DAY_1/EX_3$ ssh -T git@github.com
- output: 

Hi ZakiMahmood! You've successfully authenticated, but GitHub does not provide shell access.

#### Question no 6:
find /usr/include -name "*.c" -exec wc -l {} + | sort -nr | head -n 5
- The find command uses -exec to directly run wc -l on every .c file found in the /usr/include directory. These line counts are then "piped" through sort to rank them numerically and head to display only the top five largest files.
