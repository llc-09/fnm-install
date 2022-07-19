###host文件位置###

C:\Windows\System32\drivers\etc

##镜像源切换##

//查看镜像源使用状态：
npm get registry
//全局切换镜像源：
npm config set registry http://registry.npm.taobao.org
//全局切换官方镜像源
npm config set registry http://www.npmjs.org

##安装fnm管理工具##
1.安装choco，用来安装fnm，以管理员身份运行cmd或者powershell

cmd运行：
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

powershell运行：
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

安装完成，运行choco或choco -? 出现版本号则安装正确，如果系统上禁止运行远程脚本（yarn也是如此），输入一下命令将执行策略设置为允许签名的远程脚本就行了

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned

安装fnm：，，安装完成输入fnm --version 查看版本号

// 使用chocolatey

choco install fnm

// 如果在使用rust，使用cargo

cargo install fnm

接下来配置环境， 以管理员身份运行

code $PROFILE

将下面语句添加到profile文件末尾，保存后即可

fnm env --use-on-cd | Out-String | Invoke-Expression
 
至此fnm安装完成，使用 fnm -help 获取相关命令
