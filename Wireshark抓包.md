## TCP 抓包


#### 一、 安装RVI

#### 1. 获取UDID

> wangdenghui-iMac:dev wangdenghui$ idevice_id -l
> 
> da4c9b44d3a5a89323de932fbe02871cad25fcb9

#### 2. 安装RVI

需要使用rvictl工具，以下步骤在mac的终端中操作

> $ ifconfig -l
> 
> lo0 gif0 stf0 XHC20 en0 en1 p2p0 awdl0 en2 en3 bridge0 utun0 en5
>
> $ rvictl -s da4c9b44d3a5a89323de932fbe02871cad25fcb9

#### 3. 开始虚拟网卡

> Starting device da4c9b44d3a5a89323de932fbe02871cad25fcb9 [SUCCEEDED] with interface rvi0
>
> $ ifconfig -l
> 
> lo0 gif0 stf0 XHC20 en0 en1 p2p0 awdl0 en2 en3 bridge0 utun0 en5 rvi0


### 二、开始抓包

#### 1. wireshark

安装成功后，此时其实可以用任何抓包工具来抓取。包括wireshark等。因为这时就会看到一个rvi0的网卡。

> 捕获->选项->去掉混合模式 选择相应网卡

#### 2.过滤

开始过滤

### 三、 结束抓包

去掉RVI这个虚拟网卡，使用下面的命令：

> $ rvictl -x da4c9b44d3a5a89323de932fbe02871cad25fcb9
>
> Stopping device da4c9b44d3a5a89323de932fbe02871cad25fcb9 [SUCCEEDED]


### 四、常见问题


#### 1. you don't have permission to capture on that device mac

 mac本本使用Wireshark去抓包的时候很悲剧的告诉我，那么我们自己修改下权限让我们有权限访问就好了.
 

	1-输入命令 'whoami'
	$ whoami
	wangdenghui
	
	2-进入 /dev 目录
	$ cd /dev
	
	3-输入命令 
	
	$ ls -la | grep bp
	
	4-输入命令 
	
	$ sudo chown wangdenghui(whoami的结果):admin bp*
	
	5-重新打开 WireShark 就ok了


### 五、参考资料

[iOS抓包-TCP](https://www.jianshu.com/p/e4165e8149ec)

[遇到权限问题](https://blog.csdn.net/flyfeng125/article/details/72394417)
