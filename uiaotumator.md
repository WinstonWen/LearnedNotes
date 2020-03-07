## Uiautomator

### 原理
	python-uiautomator2主要分为两个部分，python客户端，移动设备
	python端: 运行脚本，并向移动设备发送HTTP请求
	移动设备：移动设备上运行了封装了uiautomator2的HTTP服务，解析收到的请求
	* 流程：
	1.移动设备上安装atx-agent, atx-agent启动uiautomator2服务进行监听
	2.在PC上编写测试脚本并执行（相当于发送HTTP请求到移动设备的server端）
	3.移动设备通过WIFI或USB接收到PC上发来的HTTP请求，执行制定的操作

整个过程
### 环境
	下载adb，并配置环境变量
	adb devices：查看已连接的手机
	pc安装：运行pip3 install -U uiautomator2 安装uiautomator2
	安卓安装atx-agent：运行python3 -m uiautomator2 init 安装apk到手机
	安装uiautomator：pip install --upgrade --pre uiautomator2
	安装wedtor用于查看手机：pip install –pre weditor
### 使用
	* 启动weditor：
	python -m weditor
	* wifi连接：
	d = u2.connect('10.0.0.1')
	* usb连接：
	d = u2.connect('123456f')  # 用adb查看到的设备号连接
	* 点击
	d.press("home") 点Home键
	d.press("back") 点Back键
	d.click(x, y) 单击
	d.double_click(x, y, 0.1) 双击，间隔0.1s
	d.long_click(x, y, 0.5) 长按0.5s，默认0.5s
	d.swipe(sx, sy, ex, ey, 0.5) 滑动0.5s,默认0.5s
	* 弹窗
	d.toast.show("Hello world", 1.0) 弹出消息窗口1s
	* xpath
	d.xpath("//android.widget.TextView").wait(10.0) 等待xpath指定的控件加载
	d.xpath("//*[@content-desc='分享']").click() 点击xpath指定的控件
	* 输入文字：
	d.send_keys('Hello')
	* 开关输入法：
	d.set_fastinput_ime(True/False) #开关的是uiautomator的输入法，即关闭后恢复手机原来的输入法
	* 截图
	d.screenshot(“home.jpg”)
### 操作
	手机开发者模式，开启点击坐标，方便开发



https://github.com/openatx/uiautomator2/blob/master/README.md