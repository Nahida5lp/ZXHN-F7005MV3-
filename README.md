# ZXHN-F7005MV3-光猫及其他通用教程（大概率）
恢复默认超密，开启telnet并固化

# 一.准备工具
## 1.usb转tll
![Image](https://github.com/user-attachments/assets/a78e016c-fafa-4797-bf1b-5bc43f57362f)

## 2.Putty软件
<img width="380" height="440" alt="Image" src="https://github.com/user-attachments/assets/7c40767f-8d2f-4461-94ba-14f9eb27d4f6" />

## 3.电脑开启telnet
<img width="484" height="492" alt="Image" src="https://github.com/user-attachments/assets/22e572e6-299d-45c3-8fe6-2c1f904da488" />

# 二。操作流程
## 1.只需要TXD（发送数据） RXD（接收数据） GND（接地）
![Image](https://github.com/user-attachments/assets/a78e016c-fafa-4797-bf1b-5bc43f57362f)

## 2.将TXD RXD GND分别连接GND离数字1最远
![Image](https://github.com/user-attachments/assets/54dd879a-0459-4511-b2bb-5ae7377581c2)

## 3.usb转ttl连接电脑后打开设备管理器查看com几（记得下载驱动）
<img width="1214" height="876" alt="Image" src="https://github.com/user-attachments/assets/d7225064-4e3a-43e6-a4ed-987967510a78" />

## 4.打开putty选择serial填入自己的com，speed选择115200
<img width="602" height="543" alt="Image" src="https://github.com/user-attachments/assets/0fe087a2-eac0-4e7a-82d0-5bdca8365255" />

## 5.连接后打开光猫不断按回车中断启动流程
  如果没有输出显示，更换TXD（发送数据） RXD（接收数据）位置
## 6.清空配置文件
  输入nand erase 0x900000 0x800000  
  这时光猫恢复出厂  
  输入reset重启光猫  
## 7.打开cmd，输入telnet 192.168.1.1进入光猫后台
  用户名：root  
  密码：Zte521  
## 8.在集采模式下修改光猫sn，mac，识别码
  返回setmac success表示修改成功
### 修改SN前4位（如HWTC）
  setmac show查看数据  
  setmac 1 2176 XXXX  

### 修改SN后8位
  setmac 1 2177 XXXXXXXX  

### 部分地区可能需要修改512/768
  setmac 1 512 XXXXXXXX  
  setmac 1 768 XXXXXX  

### 注册ITMS劫持（防止改完又被覆盖）：
  sendcmd 1 DB set PDTCTUSERINFO 0 Status 0  
  sendcmd 1 DB set PDTCTUSERINFO 0 Result 1

### 确保配置写入闪存
  sendcmd 1 DB save  

## 9.修改光猫地区，改完会重启
  cat /etc/init.d/regioncode  
## 10.浏览器登入光猫后台
  浏览器搜索：192.168.1.1  
  用户名：CMCCAdmin  
  密码：aDm8H%MdA  

## 11.进入后删除tr069，创建新建wan连接
  VLAN模式改写，填入VLAN ID, MTU, 输入自己宽带账密，

# 如果感到教程有用，感谢能帮助到你
  ## 感谢您的赞助
  
<div style="display: flex; gap: 10px; align-items: flex-start;">
  <img src="https://github.com/user-attachments/assets/73bec82a-3bdd-43e2-9c20-a4f3d2567216" alt="图片1" width="250">
  <img src="https://github.com/user-attachments/assets/e0579808-e933-427b-92f1-9a93e3612487" alt="图片2" width="300">
</div>
