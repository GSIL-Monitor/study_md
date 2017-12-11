

SVN的标准目录结构：欲了解详细，请参照：http://www.cnmiss.cn/?p=296

* **Trunk(主干库)**：存放核心项目
* **Branches(分支库)**：存放为不同用户客订制化的版本、或阶段性的稳定 release 版本。这些版本是可以继续进行开发和维护的
* Tag(基线库)：存档目录(不允许修改)
* Release(发布库)：存放历次发布内容



##### 主干: 

svn://192.168.100.212/xxws-web/trunk



##### 新建分支branch1

```
# 巡线卫士
svn cp svn://192.168.100.212/xxws-web/trunk svn://192.168.100.212/xxws-web/branch1 -m "create branch1 version"

# 新汽
svn cp https://svn.jasgroup.cn/svn/Project-XQGD201706/code/1.dev/trunk https://svn.jasgroup.cn/svn/Project-XQGD201706/code/1.dev/branches/branch1 -m "create branch1 version "
```

branch1下就会有trunk上的完整代码, 互不影响



##### 删除分支branch1

```
# 巡线卫士
svn rm svn://192.168.100.212/xxws-web/branch1 -m "remove branch1"

# 新汽
svn rm https://svn.jasgroup.cn/svn/Project-XQGD201706/code/1.dev/branches/branch1 -m "remove branch1"
```



##### 检出分支branch1来开发: 

```
svn co svn://192.168.100.212/xxws-web/branch1
```



##### 合并主干上的最新代码到分支上

```
# 进入分支目录
cd branch1

svn merge svn://192.168.100.212/xxws-web/trunk

# 预览该刷新操作
svn mergeinfo svn://192.168.100.212/xxws-web/trunk --show-revs eligible
```



##### 分支合并到主干

```
# 进入主干目录
cd trunk
svn merge --reintegrate svn://192.168.100.212/xxws-web/branch1
```

分支合并到主干中完成后应当删该分支，因为在SVN中该分支已经不能进行刷新也不能合并到主干 ? ? ?



##### 合并版本并将合并后的结果应用到现有的分支上

```
svn -r 148:149 merge http://svn_server/xxx_repository/trunk
```



192.168.100.212/xxws-web/trunk
192.168.100.212/xxws-web/branch

https://svn.jasgroup.cn/svn/Project-XQGD201706/code/1.dev/trunk/pepms05
https://192.168.10.200/svn/Project-XQGD201706/code/1.dev/branch/pepms05s