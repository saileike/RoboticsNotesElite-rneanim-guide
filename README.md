# RoboticsNotesElite-rneanim-guide

不是码农所以不是很懂GitHub的规范，请见谅

该项目为针对https://github.com/drdaxxy/rneanim 项目的中文使用指南，此项目用于查看机器人笔记elite PSV版本的人物模型动画。
由于此项目时间过于久远和语言原因我折腾了一两天才搞明白怎么用，虽然用的人很少，但为了防止有人和我一样走弯路浪费时间，所以还是来写一篇指南帮助有需要的人。

# 1.首先在remain项目中下载代码的ZIP压缩包，并解压在纯英文路径中
<img width="1571" height="694" alt="1" src="https://github.com/user-attachments/assets/4947c7c0-4055-418c-9812-d1f55eef1b92" />

# 2.下载psv版本的机器人笔记elite并进行一层解密
	rneanim项目用于查看的是PSV版本的机器人笔记elite中的人物模型，所以PC版和PS3版本都不可以
	本项目不提供游戏，源文件游戏的汉化版本可以在贴吧等网站中找到，保险起见我们这边使用日文原版的游戏文件进行。
	日文游戏这边采用使用 Vita3K / NPS (NoPayStation) 资源库进行获取。如果有其他方便的方法也可以，这边采用我当时成功时的方法进行演示。
  <img width="2055" height="1005" alt="Snipaste_2026-09-27_13-51-54" src="https://github.com/user-attachments/assets/676392a4-fc6c-4120-97bc-df0e34b9e3b8" />
  <img width="1784" height="899" alt="0d4171b7-ac69-46b9-bad6-497438e7b2c2" src="https://github.com/user-attachments/assets/ad946944-d2c2-4152-a2eb-c98a608e2c3f" />

*进入NPShttps://nopaystation.com/下载PC客户端，点击打开随后在弹出来的options页面中进行设置（填入数据源网址TSV 链接和解密工具）

*在Game栏下方的PSV tsv中填写https://nopaystation.com/tsv/PSV_GAMES.tsv

*点击Download and unpack dir右侧的Browse按钮，选择下载文件的保存目录

*配置 pkg2zip 解密解包工具
	通过该链接https://github.com/mmozeiko/pkg2zip 下载发行版的pkg2zip v1.8版本，解压后放在英文路径内
	点击Any pkg dec tool右侧的Browse按钮，选中下载解压好的pkg2zip.exe文件

*点击下方的Sync now按钮，完成配置

*在主页面的上方搜索PCSG00352（机器人笔记 Elite的PSVID）或 Robotics;Notes Elite 并下载	
	下载完后程序会自动进行解密并放在之前选择下载文件的保存目录下\app\PCSG00352文件夹内
	
# 3.解除文件的PFS保护
	文件依然是处于加密状态的，因此普通的 CPK 解包软件（如 CriPakTools 或 CriPakGUI）会提示损坏或打不开。
	需要先对整个游戏目录进行解密（PFS Decrypt），才能正常解包 CPK。
	（Gemini说的，具体我也不大清楚，总之现在的cpk文件是用解包软件打不开的）

*下载通过网址下载vita3k https://vita3k.org/ 的x64版本
	解压并打开exe，无需下载固件，直接点击确定
	该程序用于模拟PSV游戏，同时也对游戏进行解密

*将之前下载好的PCSG00352文件内拖入界面内，程序自动开始解密

*解密完成后主界面出现机器人笔记elite的应用图标，右键打开游戏根目录（注意不是之前下载的PCSG00352）

*找到目录下方的gamedata/model.cpk
	现在model.cpk已经被成功解密了，可以用解包软件查看了

# 4.解包cpk文件
  
  对文件进行解包
	
  下载GARbro解包软件 https://github.com/morkt/garbro 并解压
	
  打开GARbro，将目录导向gamedata/model.cpk，双击页面内的model.cpk
	
  （如果操作正确，现在可以看到cpk文件内的b001_000.cpk等文件）

*提取c001_010.cpk到c017_040.cpk等文件
	在硬盘内新建文件夹名称任意（这里假设为X）
	按住Shift左键c001_010.cpk和c017_040.cpk，选中c001_010.cpk到c017_040.cpk等文件
	右键点击提取，在第二个页面不更改默认选项，点击提取，目录选定到X文件夹内
	
# 5.整理cpk文件
	打开我们之前下载的rneanim-master文件的 D:\rneanim-master\models目录内能看到README里有这样一句话
	Recursively extract model.cpk here, using 4-digit decimal names with no extension for unnamed files, e.g. /models/c002_010/0000 for Aki's standard model.
	我们需要将刚刚X文件夹内提取出来的各文件进行二次提取和整理，需要把rneanim-master的models目录内用文件夹的形式整理好每个人物的模型动画素材

*下载本项目发行包内文件
	将create_cpk_folders文件放入X文件夹内，并运行，他会根据cpk文件名称生成相对于的文件夹

*再次使用GARbro
	打开c001_010.cpk，并将文件内的00000、00001等所有文件提取到与001_010同名的文件夹内
	其余的cpk文件都这样提取

*使用remove_zero对文件重命名
	不知道为什么rneanim/models/c002_010/0000内需要的文件名是四位数，但我们提取出来的是五位数，所以用该程序删除第一位数字0，确保每个文件都是四位数
	将remove_zero放入X//c001_010/文件夹内并运行，删除第一位数字0
	其他文件夹以此类推

*以上两个文件都是我用Gemini写的，没用其他电脑测试过，请见谅
<img width="620" height="355" alt="Snipaste_2026-09-27_14-46-47" src="https://github.com/user-attachments/assets/58089b83-c586-4eac-a857-7248dc118515" />

# 6.将我们做好的X文件夹内的文件拖入到rneanim/models/目录下，CPK文件不需要
	文件格式应该为rneanim-master\models\c001_010 以此类推

# 7.部署网络服务器
	原文Make this root folder available on a webserver (viewing index.html locally will not work)
	此项目需要将此根文件夹部署到网络服务器上才能正常工作，这边采用python的方法进行演示
	python如何下载请去网上找教程吧，当然有其他方法也可以运行，这边不是很清楚所以不教学了

*打开进入rneanim-master文件夹。

*在顶部文件路径地址栏点击空白处，输入 cmd 并按回车。

*在弹出的黑色命令行窗口中，输入以下命令并按回车：

  python -m http.server 8000

*提示运行成功后在浏览器输入网址进入

  http://localhost:8000

# 8.使用rnemain
	如果没有意外现在应该可以正常运行rneanim了
	此项目的模型浏览时会发现眼睛没有高光，算是小瑕疵
	
总之非常感谢你看到最后！

