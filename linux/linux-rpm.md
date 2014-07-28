Linux RPM安装与卸载命令
=========================

RPM（Red Hat Package Manager）
命令：rpm
1、查询、检查软件包
rpm {-q|--query} [select-options] [query-options]
rpm {-V|--verify} [select-options] [verify-options]
2、安装、升级、删除软件包
rpm {-i|--install} [install-options] PACKAGE_FILE ...
rpm {-U|--upgrade} [install-options] PACKAGE_FILE ...
rpm {-F|--freshen} [install-options] PACKAGE_FILE ...
rpm {-e|--erase} [--allmatches] [--nodeps] [--noscripts]
   [--notriggers] [--repackage] [--test] PACKAGE_NAME ...
3、其他
rpm {--initdb|--rebuilddb}
rpm {--addsign|--resign} PACKAGE_FILE ...
rpm {--querytags|--showrc}
rpm {--setperms|--setugids} PACKAGE_NAME ...
RPM（Red Hat Package Manager）
命令：rpm
select-options
         [PACKAGE_NAME] [-a,--all] [-f,--file FILE]
         [-g,--group GROUP] {-p,--package PACKAGE_FILE]
         [--fileid MD5] [--hdrid SHA1] [--pkgid MD5] [--tid TID]
         [--querybynumber HDRNUM] [--triggeredby PACKAGE_NAME]
         [--whatprovides CAPABILITY] [--whatrequires CAPABILITY]
query-options
         [--changelog] [-c,--configfiles] [-d,--docfiles] [--dump]
         [--filesbypkg] [-i,--info] [--last] [-l,--list]
         [--provides] [--qf,--queryformat QUERYFMT]
         [-R,--requires] [--scripts] [-s,--state]
         [--triggers,--triggerscripts]
verify-options
         [--nodeps] [--nofiles] [--noscripts]
         [--nodigest] [--nosignature]
         [--nolinkto] [--nomd5] [--nosize] [--nouser]
         [--nogroup] [--nomtime] [--nomode] [--nordev]
RPM（Red Hat Package Manager）
命令：rpm
install-options
         [--aid] [--allfiles] [--badreloc] [--excludepath OLDPATH]
         [--excludedocs] [--force] [-h,--hash]
         [--ignoresize] [--ignorearch] [--ignoreos]
         [--includedocs] [--justdb] [--nodeps]
         [--nodigest] [--nosignature] [--nosuggest]
         [--noorder] [--noscripts] [--notriggers]
         [--oldpackage] [--percent] [--prefix NEWPATH]
         [--relocate OLDPATH=NEWPATH]
         [--repackage] [--replacefiles] [--replacepkgs]
         [--test]

【示例】
rpm -v    显示rpm程序的详细信息
rpm --version   显示rpm的版本号
rpm -qa    显示系统中安装的所有软件包
rpm -q gcc   查询指定软件包是否已安装
rpm -qi gcc   显示指定软件包的详细信息
RPM（Red Hat Package Manager）
命令：rpm
rpm -ql gcc    显示指定软件包所包含的文件列表
rpm -qf /usr/lib/bash   查看指定文件所属的软件包
rpm -qp /tmp/webmin.rpm   查询RPM包文件中的文件信息
rpm -i webmin-1.290-1.noarch.rpm   安装指定的RPM包
rpm -ivh webmin-1.290-1.noarch.rpm 安装并显示详信息
rpm -ivh --test webmin-1.290-1.noarch.rpm 对安装进行测试，并不是安装
rpm -ivh --replacepkgs webmin-1.290-1.noarch.rpm 
软件包重复安装将会失败，若仍需要安装必须加--replacepkgs 
rpm -ivh --replacefiles webmin-1.290-1.noarch.rpm 
软件包的某个文件已在安装其他软件包时安装过，则安装将会失败，若仍需要安装必须加--replacefiles 
rpm -ivh --nodeps webmin-1.290-1.noarch.rpm 
软件包所依赖的软件包未安装，则安装将会失败，若仍需要安装必须加—nodeps
rpm -ivh --force webmin-1.290-1.noarch.rpm 强制安装指定软件包
     （忽略软件包依赖性和文件冲突，不建议）
RPM（Red Hat Package Manager）
命令：rpm
rpm –U webmin-1.29   升级指定的软件包
rpm –Uvh webmin-1.29   升级指定的软件包（显示详细信息）

rpm -e webmin-1.29   删除指定的软件包
rpm -V webmin    验证软件包webmin
rpm -Vf /bin/vi    验证包含指定文件的软件包是否正确
rpm -Va     验证所有已经安装的软件包
rpm -Vp webmin.rpm   利用RPM文件验证软件包
注：如校验正确将没有任何输出（.表示验证通过）
5 MD5校验
S 文件尺寸
L 符号链接
T 文件修改日期
D 设备
U 用户
G 用户组
M 模式（包括权限和文件类型）