## 如何把url推代码形式换成ssh
***

- 打开本地终端生成一个sshkey，在~/.ssh文件夹里会生成id_rsa（私钥）和id_rsa.pub（公钥）
    ```shell
    ssh-keygen  -C"github注册邮箱"
    ```
- 把公钥放到github上
![新增ssh公钥](./assets/github%20add%20ssh%20button.png)
- 测试ssh链接
  1. 打开终端
  2. 输入
        ```shell
        $ ssh -T git@github.com
        ```
        你会看到
        ```shell
            > The authenticity of host 'github.com (IP ADDRESS)' can't be established.
            > RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
            > Are you sure you want to continue connecting (yes/no)?
        ```
   3. 输入yes
        ```shell
        > Hi USERNAME! You've successfully authenticated, but GitHub does not
        > provide shell access.
        ```
- 如果有设置url的remote origin, 则删除url的，切换成ssh的
    ```shell
    # 删除
    git remote rm origin
    # push到远程仓库
    git push -u origin master
    ```