## 常用命令
1. ctrl c: 取消命令，并且换行
2. ctrl u: 清空本行命令
3. tab键：可以补全命令和文件名，快速按两下tab键，可以显示备选选项
4. ls: 列出当前目录下所有文件，蓝色的是文件夹，白色的是普通文件，绿色的是可执行文件 
5. ls -a：显示全部文件包括隐藏文件
6. la： 显示当前路径下面的所有文件 与 ls -a几乎一样
7. pwd: 显示当前路径
8. cd XXX: 进入XXX目录下, cd .. 返回上层目录
9. cp XXX YYY: 将XXX文件复制成YYY，XXX和YYY可以是一个路径
10. cp XXX YYY -r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
11. mkdir XXX: 创建目录XXX
12. mkdir XXX -p：确保目录名称存在，不存在的就建一个。
13. rm XXX: 删除普通文件
14. rm XXX -r: 删除文件夹
15. rm XXX -f: 直接删除
16. mv XXX YYY: 将XXX文件移动到YYY，和cp命令一样，XXX和YYY可以是一个路径；重命名也是用这个命令
17. touch XXX: 创建一个文件
18. cat XXX: 展示文件XXX中的内容

---

## tmux

1. tmux：新建一个session，其中包含一个window，window中包含一个pane，pane里打开了一个shell对话框。
2. 按下Ctrl + a后手指松开，然后按%：将当前pane左右平分成两个pane。
3. 按下Ctrl + a后手指松开，然后按"（注意是双引号"）：将当前pane上下平分成两个pane。
4. Ctrl + d：关闭当前pane；如果当前window的所有pane均已关闭，则自动关闭window；如果当前session的所有window均已关闭，则自动关闭session。
5. 鼠标点击可以选pane。
6. 按下ctrl + a后手指松开，然后按方向键：选择相邻的pane。
7. 鼠标拖动pane之间的分割线，可以调整分割线的位置。
8. 按住ctrl + a的同时按方向键，可以调整pane之间分割线的位置。
9. 按下ctrl + a后手指松开，然后按z：将当前pane全屏/取消全屏。
10. 按下ctrl + a后手指松开，然后按d：挂起当前session。
11. tmux a：打开之前挂起的session。
12. 按下ctrl + a后手指松开，然后按s：选择其它session。

方向键 —— 上：选择上一项 session/window/pane
        方向键 —— 下：选择下一项 session/window/pane
        方向键 —— 右：展开当前项 session/window
        方向键 —— 左：闭合当前项 session/window

13. 按下Ctrl + a后手指松开，然后按c：在当前session中创建一个新的window。
14. 按下Ctrl + a后手指松开，然后按w：选择其他window，操作方法与(12)完全相同。
15. 按下Ctrl + a后手指松开，然后按PageUp：翻阅当前pane内的内容。
16. 鼠标滚轮：翻阅当前pane内的内容。
17. 在tmux中选中文本时，需要按住shift键。
18. tmux中复制/粘贴文本的通用方式：

        (1) 按下Ctrl + a后松开手指，然后按[
        (2) 用鼠标选中文本，被选中的文本会被自动复制到tmux的剪贴板
        (3) 按下Ctrl + a后松开手指，然后按]，会将剪贴板中的内容粘贴到光标处

---

## vim

1. vim filename 创建一个名为filename文件
2. i：进入编辑模式
3. ESC：进入一般命令模式
4. h 或 左箭头键：光标向左移动一个字符
5. j 或 向下箭头：光标向下移动一个字符
6. k 或 向上箭头：光标向上移动一个字符
7. l 或 向右箭头：光标向右移动一个字符
8. n<Space>：n表示数字，按下数字后再按空格，光标会向右移动这一行的n个字符
9. 0 或 功能键[Home]：光标移动到本行开头
10. $ 或 功能键[End]：光标移动到本行末尾
11.  G：光标移动到最后一行
12. :n 或 nG：n为数字，光标移动到第n行
13. gg：光标移动到第一行，相当于1G
14. n<Enter>：n为数字，光标向下移动n行
15. /word：向光标之下寻找第一个值为word的字符串。
16. ?word：向光标之上寻找第一个值为word的字符串。
17. n：重复前一个查找操作
18. N：反向重复前一个查找操作
19. :n1,n2s/word1/word2/g：n1与n2为数字，在第n1行与n2行之间寻找word1这个字符串，并将该字符串替换为word2
20. :1,$s/word1/word2/g：将全文的word1替换为word2
21. :1,$s/word1/word2/gc：将全文的word1替换为word2，且在替换前要求用户确认。
22. v：选中文本
23. d：删除选中的文本
24. dd: 删除当前行
25. y：复制选中的文本
26. yy: 复制当前行
27. p: 将复制的数据在光标的下一行/下一个位置粘贴
28. u：撤销
29. Ctrl + r：取消撤销
30. 大于号 >：将选中的文本整体向右缩进一次
31. 小于号 <：将选中的文本整体向左缩进一次
32. :w 保存
33. :w! 强制保存
34. :q 退出
35. :q! 强制退出
36. 保存并退出
37. :set paste 设置成粘贴模式，取消代码自动缩进
38. :set nopaste 取消粘贴模式，开启代码自动缩进
39. :set nu 显示行号
40. :set nonu 隐藏行号
41. gg=G：将全文代码格式化
42. :noh 关闭查找关键词高亮
43. Ctrl + q：当vim卡死时，可以取消当前正在执行的命令

异常处理：
每次用vim编辑文件时，会自动创建一个.filename.swp的临时文件。
如果打开某个文件时，该文件的swp文件已存在，则会报错。此时解决办法有两种：
        (1) 找到正在打开该文件的程序，并退出
        (2) 直接删掉该swp文件即可

---

## shell
Linux系统中一般默认使用bash。
文件开头需要写#! /bin/bash，指明bash为脚本解释器。
### 注释
单行注释：每行中#之后的内容均是注释。
多行注释：
:<<EOF
第一行注释
第二行注释
第三行注释
EOF
其中EOF可以换成其它任意字符串。

### 变量

1. 定义变量

变量名=值 ：中间不能有空格。

2. 使用变量

需要加上$符号，或者${}符号。花括号可选。

3. 只读变量

readonly XXX
declare XXX
可以将变量XXX变为只读。

4. 删除变量

unset XXX ：可以删除变量XXX。

5. 变量类型

自定义变量（局部变量）子进程不能访问的变量
环境变量（全局变量）子进程可以访问的变量
自定义变量 -> 全局变量
export name  
declare -x name 
全局变量 -> 自定义变量：
 declare + XXX　

6. 字符串

字符串可以用单引号，也可以用双引号，也可以不用引号。
单引号与双引号的区别：
单引号中的内容会原样输出，不会执行、不会取变量；
双引号中的内容可以执行、可以取变量；
${#string}：字符串长度

7. 默认变量

在执行shell脚本时，可以向脚本传递参数。$1是第一个参数，$2是第二个参数，以此类推。特殊的，$0是文件名（包含路径）。

| 参数 | 说明 |
| --- | --- |
| $# | 代表文件传入的参数个数 |
| $* | 由所有参数构成的用空格隔开的字符串 |
| $@ | 每个参数分别用双引号括起来的字符串 |
| $$ | 脚本当前运行的进程ID |
| $? | 上一条命令的退出状态（注意不是stdout，而是exit code）。0表示正常退出，其他值表示错误 |
| $(command) | 返回command这条命令的stdout（可嵌套） |
| `command`	 | 返回command这条命令的stdout（不可嵌套） |

### 数组
数组用小括号表示，元素之间用空格隔开
读取数组的某个值：${array[index]}
数组长度：${#array[*]} / ${#array[@]}

### expr表达式
expr命令用于求表达式的值，格式为：expr 表达式
表达式说明：
用空格隔开每一项、对包含空格和其他特殊字符的字符串要用引号括起来。
expr会在stdout中输出结果。如果为逻辑关系表达式，则结果为真，stdout为1，否则为0。
expr的exit code：如果为逻辑关系表达式，则结果为真，exit code为0，否则为1。

1. 字符串表达式

length XXX：返回字符串XXX的长度 
`echo `expr length "$str"`  # 求字符串str长度`
index XXX YYY:  返回YYY中所有字符在XXX中第一次出现的位置，未出现返回0
`echo `expr index "$str" asd`  # 求asd每个字符在str中第一次出现的位置，下标从1开始`
substr XXX x y：返回XXX中x到y字串 
`echo `expr substr "$str" 2 3`  # 输出 str下标从2到3的字串，下标从1开始`

2. 整数表达式

expr支持普通的算术操作，算术表达式优先级低于字符串表达式，高于逻辑关系表达式。
加，减，乘，除，取模运算。两端参数会转换为整数，如果转换失败则报错。
() 可以该表优先级，但需要用反斜杠转义， 乘法也需要转义
3.逻辑关系表达式
| 与 、& 或 都具有短路规则
< <= = == != >= >  尝试将两端参数转换为整数，并做算术比较，如果转换失败，则按字符集排序规则做字符比较。
( ) 可以该表优先级，但需要用反斜杠转义
### 常用命令

1. read

用于从标准输入中读取单行数据。当读到文件结束符时，exit code为1，否则为0。
read -p：后面可以接提示信息
read -t：后面跟秒数，定义输入字符的等待时间，超过等待时间后会自动忽略此命令

2. echo

用于输出字符串。
显示普通字符串 `echo "XXX"`
显示转义字符 `echo "\"hhh\""`
输出变量 `echo $name`
显示结果定向至文件 `echo "hhh" > hello.txt`
显示命令执行结果 `echo `date``

3. test命令 用exit code返回结果，0表示真，非0表示假。

逻辑运算符 && 表示与，|| 表示或 都具有短路原则。

   - 文件类型判断

`test -e filename  # 判断文件是否存在`
`test -f filename  # 判断文件是否为文件`
`test -d filename  # 判断文件是否为目录`

   - 文件权限判断

`test -r filename  # 判断文件是否可读`
`test -w filename  # 判断文件是否为可写`
`test -x filename  # 判断文件是否为可执行文件`
`test -s filename  # 判断文件是否为非空文件`

   - 字符串判断

`test str1 == str2 # 判断字符串str1是否等于字符串str2`
`test str1 != str2 # 判断字符串str1是否不等于字符串str2`

   - 整数间的比较

`test $a -eq $b  # a是否等于b`
`test $a -ne $b  # a是否不等于b`
`test $a -gt $b  # a是否大于b`
`test $a -lt $b  # a是否小于b`
`test $a -ge $b  # a是否大于等于b`
`test $a -le $b  # a是否小于等于b`

   - 多重条件判定

`test -r filename -a -x filename #两边同时成立，返回真，否则返回假`
`test -r filename -o -x filename #两边有一个成立，返回真，否则返回假`
`test ！-r filename #取非`

   - 判断符号[]

[]与test用法几乎一模一样，更常用于if语句中。
[]内的每一项都要用空格隔开
中括号内的变量，最好用双引号括起来
中括号内的常数，最好用单或双引号括起来

4. exit

可以退出当前shell进程，并返回一个值，取值范围 0-255，0表示正常 可以用 $? 接收

### 判断语句
#### if…then
if可以嵌套格式类似C++

- 单层if
```bash
if condition
then
    语句1
    语句2
    ...
fi
```

- if-else
```bash
if condition
then
    语句1
    语句2
    ...
else
    语句1
    语句2
    ...
fi
```
#### case-esac
类似C++中的switch语句
```bash
case $变量名称 in
    值1)
        语句1
        语句2
        ...
        ;;  # 类似于C/C++中的break
    值2)
        语句1
        语句2
        ...
        ;;
    *)  # 类似于C/C++中的default
        语句1
        语句2
        ...
        ;;
esac
```

### 循环语句
break命令跳出当前循环，不能跳出case语句
continue命令结束当前循环
#### for...in
```bash
for i in v1 v2 v3
do
    语句1
    语句2
    ...
done
```
#### for ((…;…;…)) do…done
```bash
for ((i = 1; i <= n; i ++))
do
    语句1
    语句2
done
```
#### while…do…done
```bash
while condition
do
    语句1
    语句2
    ...
done
```
#### until…do…done循环
```bash
until condition
do
    语句1
    语句2
    ...
done
```

### 函数
return 的值返回的是exit code 取值范围0-255 0表示正常 
函数的输出结果可以通过 echo $(function_name)
函数的返回值可以通过 $?来获取
定义局部变量 local 变量名=变量值
```bash
[function] func_name() 
{  # function关键字可以省略
   # 在函数内，$1表示第一个输入参数，$2表示第二个输入参数, 以此类推
   # 函数调用 function_name 参数1 参数2
    语句1
    语句2
    ...
}
```
### 文件重定向
command > file	将stdout重定向到file中
command < file	将stdin重定向到file中
command >> file	将stdout以追加方式重定向到file中
### 引入外部脚本
```bash
. filename  # 注意点和文件名之间有一个空格

或

source filename

```
## ssh
### ssh登录

- 基本用法

`ssh 用户名@IP地址或域名`

- 配置文件

在~/.ssh/config中添加（没有可以创建该文件）
Host 别名
    HostName IP地址或域名
    User 用户名

- 免密登录

ssh-keygen
执行结束后，~/.ssh/目录下会多两个文件：
id_rsa：私钥
id_rsa.pub：公钥
想免密码登录哪个服务器，就将公钥传给哪个服务器的~/.ssh/authorized_keys文件里即可。
`ssh-copy-id 服务器名 #一键复制公钥`
### scp

- 基本用法

`scp source destination #将source路径下的文件复制到destination中`
`scp -r XXX YYY #复制文件夹`
`scp -P 22 XXX YYY #指定端口号`
scp的-r -P等参数尽量加在source和destination之前。
## git
### 基本概念

- 工作区：仓库的目录。工作区是独立于各个分支的。
- 暂存区：数据暂时存放的区域，类似于工作区写入版本库前的缓存区。暂存区是独立于各个分支的。
- 版本库：存放所有已经提交到本地仓库的代码版本
- 版本结构：树结构，树中每个节点代表一个代码版本。
### 常用命令
git config --global user.name xxx：设置全局用户名，信息记录在~/.gitconfig文件中
git config --global user.email xxx@xxx.com：设置全局邮箱地址，信息记录在~/.gitconfig文件中
git init：将当前目录配置成git仓库，信息记录在隐藏的.git文件夹中
git add XX：将XX文件添加到暂存区
git add .：将所有待加入暂存区的文件加入暂存区
git commit -m "给自己看的备注信息"：将暂存区的内容提交到当前分支
git rm --cached XX：将文件从仓库索引目录中删掉
git status：查看仓库状态
git diff XX：查看XX文件相对于暂存区修改了哪些内容
git log：查看当前分支的所有版本
git reflog：查看HEAD指针的移动历史（包括被回滚的版本）
git reset --hard HEAD^ 或 git reset --hard HEAD~：将代码库回滚到上一个版本
git reset --hard HEAD^^：往上回滚两次，以此类推
git reset --hard HEAD~100：往上回滚100个版本
git reset --hard 版本号：回滚到某一特定版本
git checkout — XX或git restore XX：将XX文件尚未加入暂存区的修改全部撤销
git remote add origin git@git.acwing.com:xxx/XXX.git：将本地仓库关联到远程仓库
git push -u (第一次需要-u以后不需要)：将当前分支推送到远程仓库 
git push origin branch_name：将本地的某个分支推送到远程仓库
git clone XXX：将远程仓库XXX下载到当前目录下 (在远程仓库复制克隆链接)
git checkout -b branch_name：创建并切换到branch_name这个分支
git branch：查看所有分支和当前所处分支
git checkout branch_name：切换到branch_name这个分支
git merge branch_name：将分支branch_name合并到当前分支上
git branch -d branch_name：删除本地仓库的branch_name分支
git branch branch_name：创建新分支
git push --set-upstream origin branch_name：设置本地的branch_name分支对应远程仓库的branch_name分支
git push -d origin branch_name：删除远程仓库的branch_name分支
git pull：将远程仓库的当前分支与本地仓库的当前分支合并
git pull origin branch_name：将远程仓库的branch_name分支与本地仓库的当前分支合并
git branch --set-upstream-to=origin/branch_name1 branch_name2：将远程的branch_name1分支与本地的branch_name2分支对应
git checkout -t origin/branch_name 将远程的branch_name分支拉取到本地
git stash：将工作区和暂存区中尚未提交的修改存入栈中
git stash apply：将栈顶存储的修改恢复到当前分支，但不删除栈顶元素
git stash drop：删除栈顶存储的修改
git stash pop：将栈顶存储的修改恢复到当前分支，同时删除栈顶元素
git stash list：查看栈中所有元素
## 管道、环境变量
### 管道
基本概念

- 管道类似于文件重定向，可以将前一个命令的stdout重定向到下一个命令的stdin。
- 管道命令仅处理stdout，会忽略stderr。
- 管道右边的命令必须能接受stdin。
- 多个管道命令可以串联。

与文件重定向的区别

- 文件重定向左边为命令，右边为文件。
- 管道左右两边均为命令，左边有stdout，右边有stdin。
### 环境变量
基本概念

- Linux系统中会用很多环境变量来记录配置信息。
- 环境变量类似于全局变量，可以被各个进程访问到。

修改
可以将修改命令放到~/.bashrc文件中。
执行source ~/.bashrc

常见环境变量

- HOME：用户的家目录。
- PATH：可执行文件（命令）的存储路径。路径与路径之间用:分隔。
## 配置docker环境
### 创建用户，并添加sudo权限

- 登录新服务器	ssh root@ip地址
- 创建用户	adduser 用户名
-  给用户分配sudo权限 usermod -aG sudo 用户名
### 配置免密登录

- 创建密钥	ssh keygen
- 复制密钥	ssh-copy-id 服务器名
### 安装tmux

- 更新软件	sudo apt-get update
- 安装tmux	sudo apt-get install tmux
### 安装docker

- 参考docker官网安装即可：[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)
- 将当前用户添加到docker用户组	sudo usermod -aG docker $USER		退出服务器，再重新登录
### 配置vim,tmux，bash环境

- 用scp将配置文件传给服务器即可
### docker命令

- 镜像

docker pull ubuntu:20.04：拉取一个镜像
docker images：列出本地所有镜像
docker image rm ubuntu:20.04 或 docker rmi ubuntu:20.04：删除镜像ubuntu:20.04
docker [container] commit CONTAINER IMAGE_NAME:TAG：创建某个container的镜像
docker save -o ubuntu_20_04.tar ubuntu:20.04：将镜像ubuntu:20.04导出到本地文件ubuntu_20_04.tar中
docker load -i ubuntu_20_04.tar：将镜像ubuntu:20.04从本地文件ubuntu_20_04.tar中加载出来

- 容器(container)

docker [container] create -it ubuntu:20.04：利用镜像ubuntu:20.04创建一个容器。
docker ps -a：查看本地的所有容器
docker [container] start CONTAINER：启动容器
docker [container] stop CONTAINER：停止容器
docker [container] restart CONTAINER：重启容器
docker [contaienr] run -itd ubuntu:20.04：创建并启动一个容器
docker [container] attach CONTAINER：进入容器
先按Ctrl-p，再按Ctrl-q可以挂起容器
docker [container] exec CONTAINER COMMAND：在容器中执行命令
docker [container] rm CONTAINER：删除容器
docker container prune：删除所有已停止的容器
docker export -o xxx.tar CONTAINER：将容器CONTAINER导出到本地文件xxx.tar中
docker import xxx.tar image_name:tag：将本地文件xxx.tar导入成镜像，并将镜像命名为image_name:tag
docker export/import与docker save/load的区别：
export/import会丢弃历史记录和元数据信息，仅保存容器当时的快照状态
save/load会保存完整记录，体积更大
docker top CONTAINER：查看某个容器内的所有进程
docker stats：查看所有容器的统计信息，包括CPU、内存、存储、网络等信息
docker cp xxx CONTAINER:xxx 或 docker cp CONTAINER:xxx xxx：在本地和容器间复制文件
docker rename CONTAINER1 CONTAINER2：重命名容器
docker update CONTAINER --memory 500MB：修改容器限制




	


