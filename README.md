#hikvision-control
本demo主要实现hikvision网络摄像机的登录、云台旋转控制、实时图片截取功能。

##库文件安装
将src-lib文件夹中的文件拷贝到系统的库文件目录，windows7目录如下：
```
C:\Windows\System32
```

##如何使用
将src-lib中的jar拷贝到项目lib目录中，将com.hxh.hikvision.api拷贝到项目源代码目录中。

示例代码如下：
```
//创建登录对象
LoginPlay lp = new LoginPlay();
//输入摄像机ip，端口，账户，密码登录
lp.doLogin("218.206.13.27", (short)8000, "admin", "12345");
	
//截取摄像机实时图片
Control.getImgSavePath("218.206.13.27", "C://img/2.jpg");
//制摄像机云台控制(开启)
Control.cloudControl("218.206.13.27", CloudCode.PAN_LEFT, CloudCode.SPEED_LV6, CloudCode.START);
try {
	Thread.sleep(1000);
} catch (InterruptedException e) {
	e.printStackTrace();
}
//制摄像机云台控制(关闭)
Control.cloudControl("218.206.13.27", CloudCode.PAN_LEFT, CloudCode.SPEED_LV6, CloudCode.END);
```
