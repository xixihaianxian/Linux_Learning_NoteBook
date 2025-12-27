## IP地址和主机名

- ### 1. 下载net-tools
  ```bash
  sudo apt install net-tools
  ```

- ### 2. ifconfig
  ```bash
  lisisi@lisisi:~/Documents/learn_note$ ifconfig
  ens33: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.52.128  netmask 255.255.255.0  broadcast 192.168.52.255
        inet6 fe80::20c:29ff:fe48:49c6  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:48:49:c6  txqueuelen 1000  (Ethernet)
        RX packets 248356  bytes 322878516 (322.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 44212  bytes 10626314 (10.6 MB)
        TX errors 0  dropped 2 overruns 0  carrier 0  collisions 0

  lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3104  bytes 242194 (242.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3104  bytes 242194 (242.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
  ```

- ### 3. 本机IP
  #### 本机的IP为 `127.0.0.1`

- ### 4. 特殊的IP
  #### `0.0.0.0` 可以代指本机的地址，也可以在端口绑定中用来确定绑定关系，在一些IP端口限制中，表示所有的IP的意思，如放行规则设置为`0.0.0.0`，表示允许任何IP访问

- ### 5. 主机名

  - #### 指令
    ```bash
    hostname
    ```

  - #### 修改主机名
    ```bash
    sudo hostnamectl set-hostname 修改之后的主机名
    ```

- ### 6. `hostnamectl`指令（附加）
  |**指令**|**作用**|
  |:---:|:---:|
  |`hostnamectl hostname`|Get system hostname|
  |`hostnamectl hostname NAME`|set system hostname|
  |`hostnamectl icon-name`|Get icon name for host|
  |`hostnamectl icon-name NAME`|set icon name for host|
  |`hostnamectl chassis`|Get chassis type for host|
  |`hostnamectl chassis NAME`|set chassis type for host|
  |`hostnamectl deployment`|Get deployment environment for host|
  |`hostnamectl deployment NAME`|set deployment environment for host|
  |`hostnamectl location`|Get location for host|
  |`ostnamectl location NAME`|set location for host|