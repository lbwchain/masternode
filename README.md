手把手教你搭建WINDOWS版本LBWCOIN的MasterNode  
  
准备工具：  
本地电脑  
远程服务器（VPS）可以是WINDOWS或ubuntu  
3888个LBW  

下面我们以WINDOWS服务器作为教程  
1，登录远程服务器（VPS），复制LBWCOIN-QT，然后打开  
依次点击“文件”---“接收地址”，然后复制你所看到的以L开头的接收地址  
  
2，打开本地电脑上的LBWCOIN-QT，发送3888个LBW到远程服务器钱包的地址内  
请注意，一定是3888个LBW，不能多，也不能少，一定要刚刚好  
发送的时候，注意不要勾选Subtract fee from amount  
  
3，等待5个确认数后，可以关闭本地电脑上的钱包  
先等待钱包同步完毕，点击“设置”---“选项”---“钱包”，将“Show Masternode Tab”前面框打钩  
点击远程服务器钱包里面的“交易记录”，选择刚才接收的那一笔交易，双击打开  
复制里面的交易ID: 
38a0cd170014edd4ec52f5619c5f410f041a22ae940d83969e6bd8db86be425b
Output index: 1  
在桌面新建文本文档，然后把刚才复制的交易ID和Output index粘贴到文本文档  
  
4，点击LBWCOIN钱包“工具”---“Debug控制台”在输入框内输入masternode genkey回车后  
会显示一串代码8u83WXzWhNuF7N6KRv818Ev3hZj53cLQ2yziKy89ovKf1VvEN8G  
复制这个代码到刚才新建的文本文档内  
  
5，点击LBWCOIN钱包“工具”---“Open Masternode Configuration File”  
按照以下示例填好参数  
Name IP:port masternodeprivkey collateral_output_txid collateral_output_index  
------------------------------------------------------------------------------------------------
以下为参数说明：  
Name：节点名称，随便填写即可  
IP：远程服务器IP，如果你不知道你的远程服务器IP，可以询问服务器提供商  
Masternodeprivkey：第4步输入masternode genkey回车后得到的一串代码  
collateral_output_txid：第3步得到的交易ID  
collateral_output_index：第3步得到的Output index值，通常是1或者0  
-------------------------------------------------------------------------------------------------
以下是我的示例文件  
best001 XXX.XXX.XXX.XXX:9095 6u83WXzWhNuF7N6KRv818Ev3hZj53cLQ2yziKy89ovKf1VvEN7G 7f92ca9de6934f58a8ef02a14caa10e5470599349aa2e61967bed6d8568aedfa 0
请按照实际改成你自己的数据  
  
6，点击LBWCOIN钱包“工具”---“Open Wallet Configuration File”  
复制下列参数到文件内  
rpcuser=root_username1  
rpcpassword=root_password1  
server=1  
daemon=1  
rpcallowip=127.0.0.1  
txindex=1  
maxconnections=15  
port=9095  
rpcport=4041  
masternode=1  
externalip=XXX.XXX.XXX.XXX:9095  
masternodeaddr=XXX.XXX.XXX.XXX:9095  
masternodeprivkey=8u83WXzWhNuF7N6KRv818Ev99hZj53cLQ2yziKy89ovKf1VvEN8G  
  
然后注意修改externalip和masternodeaddr参数，修改成自己远程服务器的IP  
masternodeprivkey的值是第4步输入masternode genkey后得到的一串代码  
  
7，点击LBWCOIN钱包左上角“文件”---退出  
然后重新打开钱包  
此刻你应该可以在钱包界面看到Masternodes，点击它  
找到My Masternodes  
选中你的主节点右键，Initialize masternode  
观察Status状态，如果状态显示“ENABLED”表示正常  
如果状态显示“PRE_ENABLED”请等待15分钟后再次检查状态是否正常  
如果你的服务器有防火墙，请将开放进/出TCP端口9050  
  
目前主节点数量较少，通常在几个小时应该能收到主节点奖励  
目前LBWCOIN奖励机制每个块1 BWCOIN  
POW能分到0.75个，主节点能分到0.25个  
  
Ubuntu版本搭建MASTERNODE教程类似。  





