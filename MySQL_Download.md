## MySQL Download

**本次MySQL基于Ubuntu**

----

- ### 1. 前往官网下载对应系统的ATP仓库配置文件（获取最新版本的MySQL）

  - #### 官网地址：https://dev.mysql.com/downloads/repo/apt/

  - #### 除了去官网直接下载之外，也可以使用`wget`来下载

    - ##### 语法
      ```bash
      wget https://dev.mysql.com/get/mysql-apt-config_0.8.36-1_all.deb
      ```

    - ##### 结果
      ![result](./material/mysql_material/1.png)

- ### 2. 安装仓库配置
  
  - ### 指令
    ```bash
    sudo dpkg -i mysql-apt-config_0.8.36-1_all.deb
    ```

  - ### 结果
    ![info](./material/mysql_material/4.png)

- ### 3. 仓库配置

  - #### 使用键盘上下键，先选择MySQL server，点击回车
    ![result](./material/mysql_material/2.png)

  - #### 找到一个自己喜欢的版本(**因为下载的APT仓库配置包不同，所以可以选择的版本也会有一定的区别**)
    ![result](./material/mysql_material/3.png)
    #### 键盘上下键选择之后，回车确定就行。

  - #### 完成以上操作之后就会返回到初始的界面，和上面一样，选择`ok`，回车确定就行了。
    ![result](./material/mysql_material/5.png)

- ### 4. 安装MySQL
  
  - #### 更新仓库
    ```bash
    sudo apt upate
    ```

  - #### 使用指令查看是否有自己选择的版本
    ```bash
    apt-cache policy mysql-server
    ```
    #### 你可以看到以下信息
    ![result](./material/mysql_material/6.png)
    | 字段 | 说明 |
    |------|------|
    | **Installed** | 当前系统是否已安装，以及安装的版本。若为 `(none)` 表示未安装。 |
    | **Candidate** | 如果你现在运行 `sudo apt install mysql-server`，APT 默认会安装这个版本（即“候选版本”）。 |
    | **Version table** | 列出所有可安装的版本，以及它们的来源和优先级。 |
    | **数字（如 500）** | APT 优先级（Preference）。数值越高，越优先被选中。默认仓库通常是 500。 |

  - #### 从图中可以看出我们刚刚选择的版本就是现在的候选版本
    ```bash
    sudo apt install mysql-server
    ```
    #### 如果你发现你要安装的版本不是默认安装的版本，可以尝试以下指令
    ```bash
    sudo apt install -f -y mysql-client=8.4* mysql-community-server=8.4*
    ```
    ![result](./material/mysql_material/9.png)

  - #### 之后会让你输入root密码（随便输入就行，随便输入一个密码就行）
    ![result](./material/mysql_material/7.png)
    #### 输入之后，键盘下键，选择`ok`，回车。

  - #### 确认密码
    ![result](./material/mysql_material/8.png)
    #### 输入之后，键盘下键，选择`ok`，回车。

- ### 5. 安装成功
  
  - #### 等待一定时间
    ![result](./material/mysql_material/10.png)
    #### 这样就算安装成功了

  - #### 测试是否安装成功
    ```bash
    mysql --version
    ```
    ![result](./material/mysql_material/11.png)