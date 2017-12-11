### KASS系统安装及配置

---

#### 安装

综合版下载地址：<http://download.kass.com.cn/KASS_Setup_ZH.exe>

下载后安装即可. 

可参考```新气项目模块清单及业务、研发工作划分20170824.xlsx```



#### 启动

安装完成后打开```KASS Manage Tools```

在系统状态选项卡中启动全部服务.

启动完成后点击访问主页或 Tomcat选项卡中的```IP:端口号``` 即可访问KASS系统默认的登录页面

例如: http://192.168.100.50:108

初始账号默认admin, 密码为空



#### 配置信息

1. admin账户登录KASS, 右上角点击 ```控制面板```

   打开```系统功能界面``` --> ```系统集成``` --> ```APP应用管理```

   添加app-accesskey描述和 密码.

   添加完成后会自动生成app-accesskey.

2. 在文档选项卡中建立目录, 结构如下.

   在attachment目录下建立自己的子系统目录, 目录名为各个项目组的**子系统标识**

3. 在项目的```framework.properties```文件中需要添加如下配置:

   ```
   #################### KASS文档管理系统配置 start ####################
   kass.upload.rootDir=/attachment
   kass.serverAddr=192.168.100.50:108
   kass.accessKey=MbVFcAVupTx2r8vp
   kass.accessPasswd=111111
   kass.executor=admin
   ##################### KASS文档管理系统配置 end #####################
   ```

   其中accessKey和accessPasswd替换为第1步中设置的. 

   serverAddr替换为 KASS文档系统安装的主机IP, 端口号默认108

   切换文件存储模式:

   ```
   fileUpload.fileSaveType=KASS
   ```

   ​