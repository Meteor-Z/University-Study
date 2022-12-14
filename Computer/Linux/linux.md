# Linux

## 基础入门

### 程序安装

通过`pacman`和`yay`进行安装

### 文件结构

#### 不可修改

1. `/`:根目录

2. `/root`:与

3. `/tmp`: 临时的文件目录

4. `/usr`: 

5. `/var`: 系统软件和程序存放的地方

#### 可以修改

1. `/bin`: 指令目录 可执行文件
2. `/boot`:核心文件和设置内容，主要用于开机加载
3. `/lib`:系统存放的函数库 头文件什么的
4. `/etc`:帐号密码等服务内容等
5. `/sbin`:还是系统指令
6. 

## 路径：

1. 相对路径：从`/`根路径开始描述
2. 相对路径： 从当前路径开始描述
   1. `./`: 当前目录
   2. `../`:上一层
3. '~':家目录

## 命令：

### linux

- `ctrl +C`:结束当前命令/线程，并换行

- `上 下 方向键`：上一个命令/下一个命令

- `tab`:补全命令

- `ls (list)`：列出当前目录下的所有文件
  
  文件类型
  
  - 蓝色：文件夹
  - 白色：普通文件
  - 绿色：可执行文件
  
  `-lh`:显示当前目录的文件的长信息(人性化)
  
  `-a (all)`: 显示隐藏文件(.开头的文件)

- `pwd`:显示在哪一个文件里面

- `cp XXX YYY`： 复制命令 复制粘贴 重命名  (如果复制文件夹的话，后面加上`-r`)

- `mkdir XXX` :创建`XXX` 文件夹
  
  - `mkdir a/b/c -p`:创建文件夹a/b/c `上 下 方向键`：上一个命令/下一个命令套着，连续创建

## 常用命令

### 系统状态

- `top`:相当于任务管理器 
- `dh -lh`:查看硬盘的使用状态
-  `free -lh`:查看内存的使用状态
- `du -sh`:查看当前目录占用磁盘空间
- `ps aux | grep 服务的名字`": 具体的查看这个进程的`PID`等信息
- `kill -9/-15 PID`：-9是立刻杀死这个进程，-15是完成善后工作然后关掉进程
- `w`:列出当前所在用户

###  权限状态

一共有十位，第一位表示是什么文件 rwx rwxrwx ：第一组是自己，同组的人，其他的人

 ###  文件搜索

- `find 文件路径 -name '*.py'`：搜索某一个文件路径下的所有`.py`文件
- ·`ag 字符串`：查找当前路径下哪一个包含这个字符串
- `wc`:统计行数，统计单词数，统计字节数
  - 可以从`stdin`中读入内容，又可以 在命令行参数中传入文件列表
  - `wc -l`:统计行数 （line）
  - `wc -w`:统计单词数（word）
  - `wc -c`:统计字节数（char）
- `watch -n 0.1 命令`：每0.1秒执行一下这个命令
- `tar -zcvf ttt.tar.gz test`:将test这个目录全部压缩承ttt.tar.gz
- `tar -zxvf ttt.tar.gz` ：解压

## tmux

### 命令

- `ctrl+b %`：左右分屏幕
- `ctrl+b "` 上下分屏
- `ctrl+d`：关闭当前`pane`，如果当前是单一的东西，会关闭上层`window`，直到关闭`session`
- `ctrl+b 方向键`：移动到其他的格子里面
- `ctrl+同时按住方向左右`：调整`tmux`的大小
- `ctrl+b z`:开启全屏/取消全屏
- `ctrl+b d`:挂起当前的`tmux`
- `ctrl+b s`:展开所有的`session`
- `ctrl+b w`:展开到所有的`window`

## vim
### 命令

- `i`:进入编辑模式
- `ESC`:进入一般命令模式
- `方向键盘和 hjkl`:移动方向
- `n space`:表示在这一行向右移动 $n$ 个字符
- `n enter`: 向下跳转$n$行
- `:n` :跳转到第n行
- `gg  G`:跳转到第一行/跳转到最后一行
- `/word`:光标之下寻找第一个是$word$的字符
- `?word`光标之上寻找第一个是`word`的字符
- `n`: 重复前一个查找操作:就是查找下一个/上一天
- `N`:反向重复查找下一个查找操作
- `:n1,n2s/word1/word2/g`  ：将$n1，n2$行之间的`word1`全部变成$word2$  $n2$ 变成$就是全文替换，
- `:n1,n2s/word1/word2/gc`  ：将$n1，n2$行之间的`word1`全部变成$word2$  $n2$ 变成$就是全文替换，加上c就是用户确定
- `v`:选中文本
- `d`:删除当前选中的文本
- `dd`:删除当前行
- `y`:复制选中的文本
- `yy`:复制这一行
- `u`:撤销
- `ctrl+r`:取消刚才的撤销
- `:w`:保存
- `:w!` 强制保存
- `q`:退出
- `q！`:强制退出
- `shift < / shift  >`:当前行左右移动
- `Ctrl+q`:救命操作

## shell 语法

### 变量

```bash
#! /bin/bash  # 添加脚本解释器
echo "Hello World" # 输出
chmod +x test.sh # 添加可执行权限 (changemod)

# 这是注释 跟Python差不多
echo "HelloWorld" # 这也是注释

# 定义变量
name="lzc" # 注意不能有空格
echo ${name} # 相当于取值

# 只读变量 
# 使用 readonly 或者 declare 可以将变量变成只读
age="18"
readonly age
declare -r age

# 删除命令 
# 使用 unset 关键字来进行删除这个关键字,后面就可以使用这个关键字了
unset name
unset age 

# 自定义变量和环境变量(全局变量）

# 自定义变量变成全局变量
name=lzc
export name # 第一种方法
declare -x name  # 第二种方法

# 全局变量变成自定义变量

export name=yxc # 定义环境变量
declare +x name #改成自定义变量

unset name
# 同时，在终端里面也可以直接使用shell语法
# 自定义变量只能在一个进程里面使用,但是全局变量可以在多个进程里面使用


# 字符串

# 单引号：会原样输出,不会执行，不会取变量
# 双引号: 内容可以改变，

# 取长度
name=lzc
echo  ${#name} # 前面加一个#就可以了~

unset name
# 取子串 （从0开始）
name=lzc
echo ${name:0:1} # 从0开始的1个字符
```

### 默认变量

```bash
# 文件参数变量

# 执行shell脚本的时候，可以直接传递参数，#0，#1 #2 这样的参数  #0 比价特殊，是文件名（包含路径）

$# # 参数穿入的个数 不包括第一个$0
$* $@ # 将所有的参数括起来然后返回
$？ # 表示退出状态
$$ # 运行的ID
$(command) # 返回command的stdout
`command` # 返回cmmmand的stdout

```

### 数组

```bash
# 数组 
# 跟JS的表达差不多，但是只支持一维数组，并且不需要指明大小

arrary=(1 abc "def" lzc) # 每一个元素用空格隔开 并且注意是小括号

# 也可以直接定义数组中的某一个元素的值
arr[0]=1;
arr[1]=abc

# 读取数组的值
echo ${arr[0]}

# 读取整个数组
${arr[*]} or ${arr[@]} # 比较喜欢用*

# 求数组的长度
${#arr[*]} or ${#arr[@]} # 比
```

### expr

```bash
# expr 可以求表达式值

# 字符串长度  $() 表示输出到标准输出流里面，就是显示在屏幕上
echo $(expr length ${string}) # 输出整个字符串的长度

# 返回任意当个字符在String中出现的位置
echo $(expr index ${string} a)

# 截取某一个字符 从1开始？
echo $(expr substr ${string} 2 3) # 输出字符串string {2，3}之间的

#进行数字求值
echo $(expr $a + $b) # 注意 expr里面没有括号了

```

### read

```bash
# 进行相关的读写

read -p "What's your name" -t n name # -p 是解释说明 -t 是等待n秒
echo "你好："${name}
```

### echo

```bash

echo -e "你好"  # -e 是开启转移

# 转移的的\
-c # 取消echo的回车
-n # 是回车
>in.txt # 重定向 输出到in.txt里面就行了

# 时间
echo $(date) # data是时间，能显示当前的时间

```

### printf

```bash
# 跟C/C++ 差不多，只不过是使用空格进行隔开
printf "%.2lf" 3.23222  # 这样就可以了
```

### test

```bash
# test 命令主要是用于判断文件类型，以及对变量进行做比较
test -命令  比较

-r 文件是否可读
-w 文件是否可写
-s 是否是非空
-x 判断是否可以执行



数值比较
test $a -eq $b
-eq equal 是否相同
-ne no equal 是否不相同
-gt greater than 是否大于
-lt less than 是否小于
-ge greater and equle 是否大于等于
-le less and equle 是否小于等于


字符串比较
test -z string 字符串是否为空 (? zero)
test -n string 是否非空   ()
test str1==str2 是否相同
test str1!=str2 是否不相同

多重判定：
-a 两条件是否同时存在  and
-o 两条件是否至少有一个成立 or
!  取反

[]可以完全取代test-
两者的形式是一样的
```

### 循环语句

```bash
# 输出 列出的几个元素

for i in a b c 11 22 33
do
	echo $i
done


# 输出当前路径下的所有文件名
for i in $( ls )
do
	echo $i
done

# 循环输出1到100 seqencue 序列的前三个单词
for i in $(seq 1 100) #  or {1..10} {a...z}
do
	echo $i
done

while read name
do
	echo $name
done

# 直接关闭进程
kill -9 PID # 直接杀掉进程


```

## SSH登录

直接 `ssh user@hostname - p 22`以用户名user的形式登录到hostname里面，然后进入的端口是22

- `ssh-copy-id myserver`:一键配置自己的公钥给服务器
- `ssh -r 自己的文件名 myserver:服务器的地址`：进行传输文件
- 通过传文件可以将自己电脑上的配置文件传送给服务器上进行配置

## Git

### 基本概念

- 工作区:仓库的目录，独立于各个分支，就是一个文件夹，跟`University-Stduy`一样
- 暂存区：工作区和版本库的缓冲
- 版本库：历史版本，是一个树，还是有一个有向图

## git命令分类整理

### 全局设置

- `git config --global user.name xxx`：设置全局用户名，信息记录在`~/.gitconfig`文件中
- `git config --global user.email xxx@xxx.com`：设置全局邮箱地址，信息记录在`~/.gitconfig`文件中
- `git init`：将当前目录配置成`git`仓库，信息记录在隐藏的`.git`文件夹中

### 常用命令

- `git add XX `：将XX文件添加到暂存区
- `git commit -m "给自己看的备注信息"`：将暂存区的内容提交到当前分支
- `git status`：查看仓库状态
- `git log`：查看当前分支的所有版本
- `git push -u (第一次需要-u以后不需要) `：将当前分支推送到远程仓库
- `git clone XXXXX`：将远程仓库XXX下载到当前目录下
- `git branch`：查看所有分支和当前所处分支

### 查看命令

- `git diff XX`：查看`XX`文件相对于暂存区修改了哪些内容
- `git status`：查看仓库状态
- `git log`：查看当前分支的所有版本
- `git log --pretty=oneline`：用一行来显示
- `git reflog`：查看`HEAD`指针的移动历史（包括被回滚的版本）
- `git branch`：查看所有分支和当前所处分支
- `git pull` ：将远程仓库的当前分支与本地仓库的当前分支合并



### 删除命令
- `git rm --cached XX`：将文件从仓库索引目录中删掉，不希望管理这个文件
- `git restore --staged xx`：将xx从暂存区里移除
- `git checkout — XX或git restore XX`：将XX文件尚未加入暂存区的修改全部撤销

### 代码回滚

- git reset --hard HEAD^ 或git reset --hard HEAD~ `：将代码库回滚到上一个版本
- git reset --hard HEAD^^：往上回滚两次，以此类推
- git reset --hard HEAD~100：往上回滚100个版本
- git reset --hard 版本号：回滚到某一特定版本

### 远程仓库

- `git remote add origin 仓库的SSH值`：将本地仓库关联到远程仓库
- `git push -u (第一次需要-u以后不需要)` ：将当前分支推送到远程仓库
- `git push origin branch_name`：将本地的某个分支推送到远程仓库
- `git clone git@git.acwing.com:xxx/XXX.git`：将远程仓库XXX下载到当前目录下
- `git push --set-upstream origin branch_name`：设置本地的branch_name分支对应远程仓库的branch_name分支
- `git push -d origin branch_name`：删除远程仓库的branch_name分支
- `git checkout -t origin/branch_name`: 将远程的branch_name分支拉取到本地
- `git pull `：将远程仓库的当前分支与本地仓库的当前分支合并
- `git pull origin branch_name`：将远程仓库的branch_name分支与本地仓库的当前分支合并
- `git branch --set-upstream-to=origin/branch_name1 branch_name2`：将远程的branch_name1分支与本地的branch_name2分支对应

### 分支命令

- `git branch branch_name`：创建新分支
- `git branch`：查看所有分支和当前所处分支
- `git checkout branch_name`：切换到`branch_name`这个分支
- `git merge branch_name`：将分支`branch_name`合并到当前分支上 (快速合并,会有冲突)
- `git branch -d branch_name`：删除本地仓库的branch_name分支
- `git push --set-upstream origin branch_name`：设置本地的`branch_name`分支对应远程仓库的branch_name分支
- `git push -d origin branch_name`：删除远程仓库的`branch_name`分支
- `git checkout -t origin/branch_name`: 将远程的`branch_name`分支拉取到本地
- `git pull `：将远程仓库的当前分支与本地仓库的当前分支合并
- `git pull origin branch_name`：将远程仓库的`branch_name`分支与本地仓库的当前分支合并
- `git branch --set-upstream-to=origin/branch_name1 branch_name2`：将远程的`branch_name1`分支与本地的`branch_name2`分支对应

### stash暂存

- `git stash`：将工作区和暂存区中尚未提交的修改存入栈中
- `git stash apply`：将栈顶存储的修改恢复到当前分支，但不删除栈顶元素
- `git stash drop`：删除栈顶存储的修改
- `git stash pop`：将栈顶存储的修改恢复到当前分支，同时删除栈顶元素
- `git stash list`：查看栈中所有元素



## 管道

类似于文件重定向，可以将一个命令的`stdout`重定向到下一个命令的`stdin`

### 要点

- 管道命令仅处理`stdout`,会忽略`stderr`
-  管道右边的命令必须只能接受`stdin`
- 多个管道命令可以串联

### 与文件重定向的区别

- 文件重定向为命令，右边为文件
- 管道左右均为命令，左边是`stdout`，右边是`stdin`

## 环境变量

###  查看

```bash
env # 显示当前用户的变量
set # 显示当前shell的变量，包括当前用户的变量
export # 显示当前导出成用户变量的shell变量
```

输出某一个环境变量的值

```bash
echo $PATH
```

### 修改

这里有两个地方可以修改环境变量`/etc/profile`和`~/.zshrc`里面

- `/etc/profile`:每一个用户都可以使用的环境变量 ，推荐是放在这里面
- `~/.zshrc`:当启动这个`bash`的时候才可以配置的环境变量

### 常见环境变量

- `HOME`:用户的家目录，设置了，自己的`家`就会改变
- `PATH`：类似于`win`的环境变量，运行命令都会从这里面开始找
- `LD_LIBRARY_PATH`：用于指定动态链接库(.so文件)的路径，其内容是以冒号分隔的路径列表。
- `C_INCLUDE_PATH`：`C`语言的头文件路径，内容是以冒号分隔的路径列表。
- `CPLUS_INCLUDE_PATH`：`CPP`的头文件路径，内容是以冒号分隔的路径列表。
- `PYTHONPATH`：`Python`导入包的路径，内容是以冒号分隔的路径列表。
- `JAVA_HOME`：`jdk`的安装目录。
- `CLASSPATH`：存放`Java`导入类的路径，内容是以冒号分隔的路径列表。

















