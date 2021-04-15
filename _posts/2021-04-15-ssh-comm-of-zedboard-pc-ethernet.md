---
layout: post
title: "SSH Communication of Zedboard and PC with Ethernet"
---

# SSH Communication of Zedboard and PC with Ethernet

Originally, I am searching for the method to do file transfer between a zedboard and pc, then I get to [this](http://svenand.blogdrives.com/archive/184.html#.YHdYQ-j7SUl). From this website, the connection between the zedboard and pc requires a modem router and 2 ethernet cable. However, I don't have 2 ethernet cables! Instead of connecting your host pc with ethernet cable, you can connect your pc to the modem router through wifi connection.

In this blog, I'm not using the modem router. The connection of my PC and Zedboard is barely an ethernet cable.

I'm using Windows 10 machine and [connect the zedboard to my PC](http://svenand.blogdrives.com/archive/172.html#.YHf8J-j7SUk) with two micro-USB cables. The communication with this channel is called "serial". To login the linux system of the zedboard, I have installed [Tera Term](https://ttssh2.osdn.jp/index.html.en) to communicate with the Zedboard.

So, the connection of my PC and the Zedboard is look like this:

![connection](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/connect_pc_zedboard.png)


## Prerequisite
### 1. Setup PetaLinux on Zedboard.
Checkout [this](http://svenand.blogdrives.com/archive/182.html#.YHf9YOj7SUk).

## File transfer between Zedboard and PC

### 1. Connect to Zedboard
Open Tera Term and connect to the Zedboard.

![tera_term_connect](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/tera_term_connect.png)

### 2. Login to the PetaLinux

![login_zedboard](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/login_zedboard.png)


### 3. Check Zedboard IP Address
Check your ethernet (eth0) IPv4 Address by typing in the following command to tera term terminal.
```bash
ifconfig
```

You will see that the IP address of your Zedboard is not setup. (If you use a modem router, the modem router will help you to setup the IP address.)

![zedboard_no_ip](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/zedboard_no_ip.png)


### 4. Set your own defined IP address
I set it to 169.254.154.249

```bash
ifconfig eth0 169.254.154.249
```

![zedboard_new_ip](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/zedboard_new_ip.png)

### 5. Check you Windows 10 PC internet status
Open you Windows 10: Control Panel > Network and Internet > Network and Sharing Center.

![win_ethernet](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/win_ethernet.png)

Then click on the "Ethernet" to confirm that your Windows 10 machine has connected to your Zedboard successfully.

![win_ethernet_enable](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/win_ethernet_enable.png)

### 6. Ping your Zedboard
Open Windows 10 CMD and test whether you can ping to your Zedboard through Ethernet by typing the following command in Windows 10 CMD.

```bash
ping 169.254.154.249
```

![ping_zedboard](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/ping_zedboard.png)

### 7. Login to Zedboard through SSH from your PC
If your Windows 10 doesn't have SSH command, checkout [this](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). You will need to use the SSH client on Windows 10 only, because the PetaLinux runs as SSH server as default.

![ssh_zedboard](/assets/2021-04-15-ssh-comm-of-zedboard-pc-ethernet/ssh_zedboard.png)

Notes: You can use the "scp" command to copy file fromt/to Zedboard.

For example, copy to Zedboard
```bash
scp <FILE-SOURCE-PATH> root@169.254.154.249:<FILE-DESTINATION-PATH>
```

Copy from Zedboard
```bash
scp root@169.254.154.249:<FILE-SOURCE-PATH> <FILE-DESTINATION-PATH>
```


## Reference
- http://svenand.blogdrives.com/archive/184.html#.YHdYQ-j7SUl
