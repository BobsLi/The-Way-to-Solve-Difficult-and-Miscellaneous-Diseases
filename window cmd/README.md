#### 无法加载文件 .ps1，因为在此系统中禁止执行脚本
解决方法：更新系统脚本执行策略 ，以管理员身份运行powershell,然后执行
```bash
	set-executionpolicy remotesigned
```
