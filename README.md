# Interplayer


**这是什么：**  
　　把网易云/qq/酷狗/酷我的歌单转移到虾米的半自动化小程序。

**为什么做这个：**  
　　直接原因是我有上百个歌单，谁想重复无意义劳动，顺便还能学selenium；  
　　间接原因是网易云是大猪蹄子；  
　　根本原因是某人。

**为什么自动化了还是有这么多手动步骤：**  
　　因为。。都说了是半自动化！  
　　并且我只是为了自己方便，所以怎么性价比高怎么来。

**如果遇到了奇怪的问题：**  
　　~~都是因为我懒得写代码处理~~ 已知的错误都已处理

**使用说明：**　　
1. 我的环境：python3/chrome+chormedriver85/selenium  
2. 先运行 cookie.py ，给你20秒手动登录一下，扫码很快的！  
3. 如果出现 xiami_cookies.txt，并且能在里面搜到你的虾米userid表示成功。搜不到说明你超过20s了，重新做步骤2等待运行完毕  
4. main.py 中  
    1. 替换上自己的虾米id driver.get("*https://emumo.xiami.com/space/import/u/<替换userid>*")  
    2. pl_links中放自己的网易云歌单的链接，支持在网易云创建的歌单和收藏的歌单，但注意导入之后都变成你在虾米创建的歌单，ps：pl_links中的第一个链接导入之后会在最后一个，最后一个会在第一个  
    3. 滑块自己拖吧，因为我懒得写,之后可能会写

----------------------------------------------

**Q&A：**  
Q：怎么获取源歌单的链接  
A：浏览器打开源音乐网站，打开到主页或者歌单页（比如网易云的主页链接是 *https://music.163.com/#/user/home?id=<你的userid>* 可以不登录，也就是说也可以导入别人的歌单），f12开console，给个适配网易云的实例（已倒序）：  
　　``count=117  // 歌单数-1``  
　　``pl=[]``  
　　``while(count>=0){console.log($$(".msk")[count].href);pl[177-count]=$$(".msk")[count].href;count--;}``  
　　``console.log(JSON.stringify(pl));``  

Q：什么？你要从qq/酷狗/酷我导入？  
A：~~源的歌单链接仍旧自己获取，放到pl_links中，剩下的我可能会写，其实很方便的啦~~ 可以导入了

Q：什么？你要导入到别的地方？  
A：自己写吧886　ps:咪咕网页版无导入功能

----------------------------------------------

**可能会产生的问题：**  
P：提示“导入失败”  
S：虾米曲库中没有该歌单的任意一首歌。每一个失败的歌单信息都会打印并且记录在fail_log中。（错误处理完成）  

P：提示“创建失败”  
S：八成是歌单有特殊字符，删掉字符后手动按下“导入歌单”即可。（错误处理完成）  

P：提示“正在帮你”  
S：八成是源歌单原本就为空。每一个失败的歌单信息都会打印并且记录在fail_log中。（错误处理完成）

P：提示“系统错误”  
S：检查一下代码中自己的虾米userid有没有替换上。没错的话，一般只重新运行一下main.py即可，记得把pl_links中已经导入的链接删掉然后重新运行。会打印头一个未成功的歌单信息并且记录在fail_log中。（错误处理完成）  

P：提示“操作频繁”  
S：实测大概导入50个之后会出现，等着吧，过段时间再继续，这个一段时间八成不是分钟级的，微笑。会打印头一个未成功的歌单信息并且记录在fail_log中。（错误处理完成）  

----------------------------------------------
----------------------------------------------

2020.10.12  
错误处理完成  
等大佬传牛逼功能中

----------------------------------------------
----------------------------------------------

2020.10.11  
源=网易云/qq/酷狗/酷我 完成
增加部分错误处理

----------------------------------------------
----------------------------------------------

2020.10.10 基本功能完成  
源=网易云

----------------------------------------------
----------------------------------------------

2020.10.9  
关键技巧：cookie自动登录  
xiami部分完成度70% netease部分未开始