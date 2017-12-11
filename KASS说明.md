### KASS说明



---



#### 1. 关于试用版过期

试用版的KASS系统时间为30天, 如果过期, 卸载后重新安装即可. 

具体步骤:

1. 在KASS系统管理程序中停止 KASS 所有相关服务
2. 运行```KASS安装目录下\unins000.exe```
3. 重启机器后删除整个KASS安装目录

**注意**: 如果想保留数据, 在删除之前提前备份两个目录:

* ```[KASS安装目录]\datas```
* ```[KASS安装目录]\mysql5.1\data```



#### 2. 迁移, 备份和还原KASS

如果迁移KASS, 或卸载后重装KASS后想要保留之前的数据文件

需要备份和还原, 具体步骤如下:

1. 备份文件及索引库：备份安装目录下的 ```datas``` 文件夹
2. 备份MYSQL数据库：停止数据库服务后，备份安装目录下的 ```mysql5.1\data``` 文件夹
3. 还原系统
   * 使用安装程序在机器上执行全新安装, 启动并检查新安装的系统是否正常运行.
   * 停止新安装系统的所有KASS相关服务
   * 将备份的数据库文件夹复制到新安装系统对应位置
   * 将备份的文件及索引库文件夹复制到新安装系统对应的位置



#### 3. 预览功能说明

文件预览, 服务器需要满足环境部署要求.

**[必须]**: 要求服务器安装 .net 框架(必须4.0版本以上)

##### office文件预览

支持office文件(```.doc, .docx, .xls, .pptx, .vsdx```)等转换为```.pdf``` 后提供浏览器预览.

服务器要支持**kofficeconvert**转换工具: 要求服务器安装 ms office 2010 或 2013



其他转换工具的说明可参考:

```
/***************************** 部署环境说明 *********************/
程序的使用环境部署要求及注意事项:
1.必须：要求服务器安装 .net 框架(必须4.0版本以上)
2.必须: 要求服务器为 windows server 2008/windows7以上操作系统.
3.kofficeconvert.exe：要求服务器安装 ms office 2010 或 2013 (至少安装 word/excel/ppt/Office共享功能, 选择 从本机运行全部程序, 安装完毕后至少手动运行过一次程序)(建议: 在服务器部署时手动设置office程序的信任中心)
4.kvisioconvert.exe: 要求服务器安装 Microsoft Office Visio 2013 (注意不能安装Visio 2010版本).
5.kmppconvert.exe: 要求服务器安装 Microsoft Project 2010
6.kwpsconvert.exe: 要求服务器安装 WPS 专业版2016 (可在WPS官方网站下载)(注意安装时去掉勾选 默认打开ms office文件的方式为wps)
7.kwpsconvert.exe(for wps2013)：要求服务器安装安装 WPS 专业版2016，需要将wps2013目录下文件复制到当前目录下（可能与OFFICE不能兼容） 将kingsoft相关DLL全部移出

/***************************** 使用注意事项 *********************/
1.程序执行命令行示例: kofficeconvert.exe -infile="d:\test.doc" -outfile="d:\test.pdf"
2.输入参数infile:  输入源文件的完整路径(注意源文件的后缀必须符合上面所列类型)
   输出参数outfile: 输出目标文件的完整路径(注意目标文件的后缀必须符合上面所列类型)
3.支持的转换方式: 
	kofficeconvert.exe:	.doc/.docx/.xls/.xlsx/.ppt/.pptx/.pps/.ppsx/.vsd/.vsdx 转为 .pdf	.xls/.xlsx 转为 .html
	kvisioconvert.exe:	.vsd/.vsdx 转为 .pdf
	kmppconvert.exe:	.mpp 转为 .pdf
	kwpsconvert.exe:	.wps/.et/.dps 转为 .pdf		.et 转为 .html
4.建议: 在服务器使用administrator账号身份来启动程序, 从交互式桌面发起运行程序.


/***************************** 返回值说明 *********************/
exit=0		转换文件成功
exit=-1		未知异常
exit=1		缺少参数
exit=2		不支持的操作类型
exit=3		依赖的程序不可用
exit=4		请稍后重新尝试
exit=5		源文件不存在
exit=6		目标文件已存在
exit=7		目标文件夹不存在
exit=8		打开文件失败
exit=9		转换文件失败
exit=10		内存不足

```





















