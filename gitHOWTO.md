# Introduction #

Git使用方法


# Details #

文档目的:让HFG的朋友们可以在上面练习一下git的基本用法,大家可以继续增加或者修改
文档作者:NalaGinrut, CityPW, Xiangfu(后来的加到后面)

# 注册帐号 #
1,到http://gitorious.org/注册帐号
2,使用ssh-keygen生成keys,然后把id\_rsa.pub文件里的内容copy到登录http://gitorious.org/网站后的dashborad的ssh
keys manage的add keys里面.
3,到http://gitorious.org/hfgtest/hfgtest申请加入,或者发邮件通知nalaginrut把你加进来.
4,就可以进行git的操作了.

# 基本操作 #
1.Clone 只读代码库命令:
> $ git clone git://gitorious.org/hfgtest/hfgtest.git
> Clone 可写代码库命令:
> > $ git clone git@gitorious.org:hfgtest/hfgtest.git

> 可以用以下命令来变换:
> > $ git remote remove origin
> > $ git remote add origin GIT\_URL\_IN**[1](1.md)
2.把服务器代码同步到本地代码库
> > $ git pull origin master
3.新建文件:
> > $ touch NEW\_FILE
> > $ git add ./NEW\_FILE
4.编辑文件README, 修改一些东东,比如加入"your name and your email"
5.提交修改到本地
> > $ git commit README -s -m "COMMIT LOG"
6.把本地代码同步到服务器
> > $ git push -u origin master
7. 发送补丁邮件：
> > 编译 .git/config 文件添加：

> [sendemail](sendemail.md)
> > smtpserver = SMTP\_SERVER\_FOR\_EXAMPLE\_smtp.gmail.com
> > smtpencryption = tls
> > smtpuser = USERNAME
> > smtppass = PASSWD
> > smtpssl = yes
> > confirm = auto

> 生成补丁邮件文件：
> > $ git format-patch -n [is the patches count](n.md)

> 发送邮件：
> > $ git send-email 0001-_.patch [xxx.patches] --to
hackerfellowship@googlegroups.com_

# 参考 #
http://www.linuxsir.org/main/doc/git/gittutorcn.htm**

# GUI #
两个图形界面 gitk, gitg. 在Debian 下安装

> $ sudo aptitude install gitk
> $ sudo aptitude install gitg

特别注意：
1、由于gitorious会自动建立名为origin的remote地址（gitorious会把origin的url自动设置为你使用git
clone的地址），所以我们仅仅需要在git
pull之前把.git/config中的url改为可提交地址git@gitorious.org:Project\_name
/Project\_name就可以了，不必再使用git remote
add，当然你也可以换个名称（比如origin2，并使用可提交的git地址）。该情况仅仅限于gitorious，并且你采用了git
clone git:// 形式的只读地址；假如你在clone之前已经获得hfg权限并提交了public ssh
key，那你可以直接使用git clone git@ 形式的可维护地址，这样。（如果还有不清楚的地方可直接询问NalaGinrut）