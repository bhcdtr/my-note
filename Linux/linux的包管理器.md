# 包管理器
>
>dpkg（底层工具）->apt-get（上层工具）->apt（apt-get的再封装）

## apt install和apt-get install的区别是什么？
>
>1.apt 命令是对之前的apt-get apt-cache 等的封装，提供更加统一，更加适合终端用户使用的接口。
>2.apt 具有更精减但足够的命令选项，而且参数选项的组织方式更为有效。
>3.apt是为交互使用而设计的。最好在shell脚本中使用apt-get和apt-cache，因为它们在不同版本之间向后兼容，并且有更多选项和功能。对于基本命令，apt和apt-get两个工具的语法是相同的。
> 如果在非交互式脚本中运行apt install，就会提示没有稳定的CLI 接口。
所以要在脚本中安装软件，用apt-get 保险一些，如果是自己在终端中使用命令行，显然是使用apt 更方便一些。

## apt 命令 取代的apt-get命令 命令的功能

```bash
apt install | apt-get install | 安装软件包
apt remove | apt-get remove | 移除软件包
apt purge | apt-get purge | 除软件包及配置文件
apt update | apt-get update | 刷新存储库索引
apt upgrade | apt-get upgrade | 升级所有可升级的软件包
apt autoremove | apt-get autoremove | 自动删除不需要的包
apt full-upgrade | apt-get dist-upgrade | 在升级软件包时自动处理依赖关系
apt search | apt-cache search | 搜索应用程序
apt show | apt-cache show | 显示安装细节
```
