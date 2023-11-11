# WinWxDump64
SharpWxDump的64bit版本。微信客户端取证，获取用户key，解密聊天记录  

# 免责声明
本项目仅允许在授权情况下对数据库进行备份，严禁用于非法目的，否则自行承担所有相关责任。使用该工具则代表默认同意该条款;

请勿利用本项目的相关技术从事非法测试，如因此产生的一切不良后果与项目作者无关。
  
## 版本支持
目前支持的最新微信版是 3.9.8.15 。暂无后续更新计划。需要的请自行重新编译，见[二次编译](#二次编译)。

## 简介  
最近捣鼓了半天成功破解了微信记录。需求是在尽可能快的情况下，拿到目标电脑的破解记录。  

这个方法在u盘插入的情况下，运行一下程序，拍张照片，拷贝一下db就可以了。后续再在另一条电脑上运行解密代码。（所以要记得及时锁屏！）

原作者的SharpWxDump似乎没有更新64位。
Hali在其基础上补全了，但是我用的时候他在issue给的代码没有更新到最新版微信。
xaoyapp的脚本基于python，需要在目标机上装python和c++。但是他的repo一直更新着新的版本号。
（具体链接请见[感谢](#感谢)）

目前的方案是，在需要更新版微信的情况下。基于Hali给的文件进行编译，

## 使用方式
0. 确保微信登录中。 
1. 打开cmd，将program.exe拖进去，回车。
2. 获得 WechatKey.
3. 找到需要解压的db文件。（如果是该账号第一次登录，一定要关闭微信，否则db文件为空。微信在每次关闭时将数据写入db。）
4. 使用decrypt.py解密。
   
   Win `py decrypt.py -k WechatKey -i db_path -o output_path`
   
   Mac `python3 decrypt.py -k WechatKey -i db_path -o output_path`
   
   详见代码本身或[xaoyaoo的PyWxDump源代码](https://github.com/xaoyaoo/PyWxDump/blob/master/pywxdump/decrypted/decrypt.py)
6. 使用数据库软件打开。推荐[DB Browser for SQLite](https://sqlitebrowser.org/dl/)

## 二次编译
1. 解压 WinWxDump64.zip， 打开Program.cs 。
2. 在代码最下方插入需求版本号的相应参数。[参数来源 xaoyaoo Repo](https://github.com/xaoyaoo/PyWxDump/blob/master/pywxdump/version_list.json)
3. cd到Program.cs所在文件夹
4. 运行 `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe .\Program.cs /platform:x64`

## 感谢  
@AdminTest0 的Repo [SharpWxDump](https://github.com/AdminTest0/SharpWxDump/tree/master)  

@hallejuyahaha 的[代码](https://github.com/AdminTest0/SharpWxDump/issues/48)  

@xaoyaoo 的Repo [PyWxDump](https://github.com/xaoyaoo/PyWxDump)
