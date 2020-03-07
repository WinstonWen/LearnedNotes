# ADB
### 简介
	adb是安卓调试桥的英文缩写，将安卓设备通过USB连接到电脑，并开启usb调试模式，即可使用
	学习资源：http://adbshell.com
### 工具
	Win 版 https://dl.google.com/android/repository/platform-tools-latest-windows.zip
	Linux 版 https://dl.google.com/android/repository/platform-tools-latest-linux.zip
	Mac 版 https://dl.google.com/android/repository/platform-tools-latest-darwin.zip
	国内用户请使用 https://pan.lanzou.com/b86819/
### adb命令
	* 查看连接设备：
	adb devices
	* 安装与卸载app：
	adb install <filename>
	adb uninstall <filname>
	* root：
	adb root
	* 进入手机shell
	adb shell # 安卓内核是linux,所以进入安卓手机的shell后和linux很像
	* 重启到 Recovery 模式：
	adb reboot recovery
	* 从 Recovery 重启到 Android：
	adb reboot
	* 重启到 Fastboot 模式：
	adb reboot bootloader
	* 文件传递：
	adb push/pull <from_file> <to_file>
### fastboot 模式下的一些命令
	* 查看连接设备：
	fastboot devices
	* 刷写分区：
	fastboot flash xxx <xxx.img>
	* 格式化分区：
	fastboot format xxx    # 慎用
	* 重启：
	fastboot reboot
	* 重启到 fastboot：
	fastboot reboot-bootloader
	* boot 引导启动：
	fastboot boot <xxx.img>
	# 其中 xxx 代表分区，可以是 recovery，system，data,cache；<xxx>.img代表镜像，某些手机需要输入 [-i] 参数，具体的请看手机论坛的教程

## 安卓系统root
### 准备
	材料：
	* 解锁bootloader的手机
	* 下载有adb的电脑
	* 下载与自己手机ROM一样的ROM包（去MIUI,Flyme下载）
	* 把系统更新到最新
	操作：
	* 提取ROM包中的boot.img文件（ROM是zip文件）
	* 手机上下载 Magisk Manager
	* 翻墙更新Magisk Manager

### 刷入Magisk
	把boot.img 传到手机
	打开Magisk Manager,点击安装Magisk，选择修补Boot（修补中需翻墙）
	修补后，在文件资源管理器，进入Download文件夹，多出patched_boot.img。移动到根目录下
	把patched_boot.img传输到电脑上，并放入adb文件夹下，手机进入fastboot模式
	pc端输入命令行：fastboot device   出现<设备号> fastboot 则手机就绪
	输入：fastboot flash boot patched_boot.img  出现finished.....则成功
	重启手机后，root成功
## 刷机
### 通过 sideload 更新系统
	1. 重启到 Recovery 模式：
	adb reboot recovery
	2. 检查是否连接成功
	3. 在设备的 Recovery 界面上操作进入 Apply update-Apply from ADB
	4. 通过 adb 上传和更新系统: adb sideload <path-to-update.zip>
	# 需要使用第三方 REC，某些官方 REC 确实也支持 adb sideload 升级，推荐使用 TWRP 的 REC。



## 引用
	https://blog.xxwhite.com/2017/AdbUsing.html
	http://www.oneplusbbs.com/thread-3198566-1.html
