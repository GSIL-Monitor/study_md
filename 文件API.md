

## 文件API



* #### 更新历史

| 更新日期       | 备注                                       |
| :--------- | :--------------------------------------- |
| 2017-09-26 |                                          |
| 2017-09-28 | 文件上传接口增加moduleCode参数                     |
| 2017-10-27 | 文件删除接口参数名修改(isShiftDeleteAttachementFile -> isShiftDelFile) |

<br><br>



#### **文件上传**

> 为业务对象上传附件

```POST /jasframework/attachment/upload.do```

参数

```
businessId: 65182414-b72c-48c3-9e2b-eac23c7f6cd6   //业务对象ID(跟在url后)
businessType: pic  //文件的业务含义(跟在url后), 不传后台默认值为"attachment"
moduleCode: samples //子系统业务模块名(跟在url后)
				   //用于上传到KASS系统中的目录分类, 不传后台默认值为"default"
file //上传的文件
```
返回
```
# 文件ID集合
{
	"status": 1,
	"rows": [
		"8df58bfa-15df-45c2-9e38-492f2fb8264a",
		"748da1e0-745b-4eed-b3ba-3a2918472f3f"
	]
}
```

<br><br>

#### 文件下载

> 根据文件ID下载

```GET /jasframework/attachment/download.do ```

参数

```
eventid: df193feb-b661-4524-8a75-373c1be5d753 //所要下载附件的eventid
```

返回

```
HttpServletResponse 中包含下载的文件
```

<br><br>

#### ~~文件预览~~

> ~~原来提供的文档预览接口, 需要FlexPaper组件支持(可以用KASS提供的预览接口)~~

~~```GET /jasframework/attachment/getPreviewFile.do```~~

参数
```
eventid: df193feb-b661-4524-8a75-373c1be5d753 
```

返回

```
response输出流
```



<br><br>

#### 文件预览

> 获得KASS系统文件预览地址

​```GET /jasframework/attachment/getPreview.do``` 

参数

```
eventid: df193feb-b661-4524-8a75-373c1be5d753 
```

返回

```
# 返回预览地址, 该url在浏览器中可直接预览
{
	"status": 1,
	"data": "http://192.168.100.50:108/kass/preview/rtiaivycfctogjwe"
}
```


<br><br>



#### 获取文件信息列表

> 据业务对象ID和文件的业务含义获取文件信息列表

​```GET /jasframework/attachment/getInfo.do```

参数

```
businessId: 65182414-b72c-48c3-9e2b-eac23c7f6cd6   //业务对象ID, (跟在url后)
businessType: pic  //文件的业务含义(跟在url后), 不传后台默认值为"attachment"
```

返回

```
{
	"status": 1,
	"rows": [{
		"fileName": "man.png",
		"fileDescription": "头像",
		"eventid": "8acd993f-949e-437d-97a5-64924719e2c7"
	},
	{
		"fileName": "阿里巴巴Java开发手册(终极版).pdf",
		"fileDescription": "规范手册阿斯顿",
		"eventid": "df193feb-b661-4524-8a75-373c1be5d753"
	}]
}
```



<br><br>

#### 获取图片缩略图

> 用指定宽度、高度或压缩比例 的方式对图片进行压缩后返回图片字节数组

​```GET /jasframework/attachment/getImageBySize.do```

参数

```
eventid: df193feb-b661-4524-8a75-373c1be5d753 //要获取缩略图文件的ID(必传)
width: 50 //压缩后图片宽度（当压缩比例rate==null时，必传）
height: 140 //压缩后图片高度（当压缩比例rate==null时，必传）
rate: 0.5 //压缩比例 (按比例率计算出width合height进行压缩0-1)
```

返回

```
byte[]字节数组
```

<br><br>



#### 文件删除

> 删除文件

​```GET /jasframework/attachment/delete.do```

参数

```
eventids: df193feb-b661-4524-8a75-373c1be5d753 //附件id,多个id使用逗号隔开
isShiftDelFile: true //是否真的删除数据，false:假删除，true:真删除
```

返回

```
# 成功
{"status":1}
```




