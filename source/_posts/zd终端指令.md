---
title: 终端指令
tags: html
categories: html
---

## vim 

一般模式，命令模式，编辑模式
按 a，就由一般模式进入编辑模式
由编辑模式退回一般模式，Esc

### 命令模式，以：开头的

:q    退出
:wq 保存退出
:q!    强制退出 （不保存退出）
:set nu   显示行号
:set nonu  隐藏行号

### 一般模式下

dd     删除一行（剪切）  ctrl+x
num  dd    删除 num 行
p   将剪切的内容粘贴到光标所在行下面
ctrl+v
yy   拷贝一行     ctrl+c
num yy  拷贝 num 行
u   撤销   undo
ctrl+r   恢复   redo
gg   定位到第一行
shift+g    定位到最后一行
num shift+g   定位到 num 行

# 整理

" / "  ：根目录
" ~ " ：用户主目录的缩写。例如当前用户为 hello，那么" ~ "展开来就是：/Users/hello
" . "  ：当前目录
".."   ：父目录
①. 进入根目录 cd ～
②. 返回上一级目录 cd ..
③. Ls 显示目录下的详细内容
ls   查看当前目录下得内容
ls /   查看根目录的内容
ls ./   查看当前目录下得内容
ls ../   查看父目录下得内容
ls ~    查看用户目录的内容（打开终端默认在用户目录下）
①. Clear 清屏
②. 新建文件夹 mkdir xxx 
③. 新建问价 touch xxx
④. Cd xxx 进入 xxx 的文件夹
⑤. 删除 rm 1.txt 删除 1.txt 的文件
⑥. rm -rf 456/  删除当前目录下 456 名字的文件夹，删除文件夹的同时，里面的文件统统删除。
⑦. vi 1.c  （如果文件存在，则打开这个文件，如果不存在，先创建，再打开）
⑧. cp 1.txt 2.txt 将当前目录下的 1.txt 拷贝一份，并放到当前目录下，并命名为 2.txt
mv  aaa bbb  将当前目录下得 aaa 文件，移动到当前目录下，并改名为 bbb
cp  aaa bbb 将当前目录下得 aaa 文件，拷贝一份，放到当前目录下，并改名为 bbb
⑨. pwd  查看当前所在的位置（目录）

# 指令

" / "  ：根目录
" ~ " ：用户主目录的缩写。例如当前用户为 hello，那么" ~ "展开来就是：/Users/hello
" . "  ：当前目录
".."   ：父目录
ls 列出当前目录下的子目录和文件
快速通过终端命令用 vscode 打开指定文件夹 进入文件夹目录后 .code
cd -   回到上一个目录
cd ~  回到用户目录(刚打开终端时的目录)
list show
ls  显示当前目录下的文件内容
ls 可以和路径配合使用，用于显示路径下的内容
ls 后面如果什么都不加，默认显示当前目录下的内容。
ls /  显示跟目录下的内容
clear 清空屏幕的内容
percent work directary
pwd  查看我们所在的目录（位置），刚打开终端的时候，默认在用户目录下。
make directory
mkdir xxx  在当前目录下，创建一个 xxx 名字的文件夹
touch aaa  在当前目录下创建一个 aaa 名字的文件
come directory
cd xxx  进入 xxx 的文件夹     (Tab 键会自动补齐)
remove
rm 1.txt  删除名字为 1.txt 的文件
rm -rf 456/  删除当前目录下 456 名字的文件夹，删除文件夹的同时，里面的文件统统删除。
(方向键上下键，可以翻看历史命令)
move
mv 1.txt 123.txt 移动+改名，将当前目录的 1.txt 移动到当前目录，并改名为 123.txt
cp 1.txt 2.txt 将当前目录下的 1.txt 拷贝一份，并放到当前目录下，并命名为 2.txt
vi （vim）
vi 1.c  （如果文件存在，则打开这个文件，如果不存在，先创建，再打开）
vi 命令有 3 种模式
命令模式   （以:打头的命令）
:q  退出，（如果文件已经被编辑了，而没有保存的话，是无法退出的）
:w  保存
:wq  保存退出
:q!   不保存退出
:set nu       显示行号
:set nonu  隐藏行号
编辑模式
由编辑模式进入一般模式，按 Esc 键
一般模式   （一般命令）
由一般模式进入编辑模式
a,i,o, shift+a,shift+i,shift+o 键
dd   删除一行(光标所在的那一行) (剪切)
5dd  删除光标下的 5 行
p    粘贴
yy   复制
5yy  复制 5 行
u      撤销上一次操作 （undo）
ctrl+r   恢复操作     (redo)
gg   将光标定位在第一行
shift+g 将光标定位到最后一行
num shift+g  将光标定位在第 num 行
ls   查看当前目录下得内容
ls /   查看根目录的内容
ls ./   查看当前目录下得内容
ls ../   查看父目录下得内容
ls ~    查看用户目录的内容（打开终端默认在用户目录下）
ls /Users/apple
pwd  查看当前所在的位置（目录）
cd  目录     进入目录文件夹
mkdir   xxx   创建一个名字为 xxx 的文件夹
touch  yyy   创建一个名字为 yyy 的文件
vi  yyy   如果文件不存在，则创建一个 yyy 的文件，并打开，如果文件存在，则是打开 yyy 文件。
rm yyy    删除 yyy 文件
rm -rf  xxx  删除 xxx 文件夹
mv  aaa bbb  将当前目录下得 aaa 文件，移动到当前目录下，并改名为 bbb
cp  aaa bbb 将当前目录下得 aaa 文件，拷贝一份，放到当前目录下，并改名为 bbb
