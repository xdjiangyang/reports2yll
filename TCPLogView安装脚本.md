上周六，即2017年5月20日主要做了两件事：



1. **调整TCPLogView的配置文件**
	
	TCPLogView的配置文件如下

		[General]
		ShowGridLines=0
		SaveFilterIndex=0
		ShowInfoTip=1
		ResolveIPAddresses=1
		TrayIcon=1
		AutoScrollDown=0
		NoLocalHost=0
		WriteToLogFile=0
		LogFilename=TcpLogView.csv
		StartAsHidden=1
		WinPos=2C 00 00 00 00 00 00 00 01 00 00 00 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 5F 01 00 00 95 00 00 00 DF 03 00 00 75 02 00 00
		Columns=78 00 00 00 64 00 01 00 78 00 02 00 78 00 03 00 96 00 04 00 64 00 05 00 64 00 06 00 64 00 07 00 96 00 08 00 2C 01 09 00 96 00 0A 00
		Sort=0

	将TrayIcon置为1，表示程序以托盘形式启动；
	
	将WriteToLogFile置为1，表示程序将结果记录到log中；

	LogFilename=TcpLogView.csv表示log名称为TcpLogView，格式是csv。


2. **编写TCPLogView的安装脚本**

	安装脚本如下：

		@echo off  

		set ProgramFilesDir="C:\Program Files"
		set RegPath="HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run"
		if /i %processor_architecture% equ amd64 (  
		set TcpLogViewFile=TcpLogView-x64.exe
		set TcpLogViewDir=tcplogview-x64
		) else (  
		set TcpLogViewFile=TcpLogView.exe
		set TcpLogViewDir=tcplogview
		)
		set TcpLogViewFullPath=%ProgramFilesDir%\%TcpLogViewDir%
		md %TcpLogViewFullPath%
		xcopy %~dp0%TcpLogViewDir% %TcpLogViewFullPath%
		reg add TcpLogView /v %TcpLogViewDir% /t REG_SZ /d %TcpLogViewFullPath%\%TcpLogViewFile%

	*主要步骤为*：
		
	- 判断CPU类型；
	
	- 分别拷贝32位程序和64位程序到相应的目录；
	
	- 添加注册表项，TCPLogView可以开机启动。
	
	*注意事项*：
	
	- **安装脚本要以Admin权限执行**