# CMDB and ansible ui

## 安装参考

- python2.7
- 使用sqlite需要初始化数据库
- 如使用mysql需要创建CMDB库，映射，修改setting数据库信息
- 安装步骤查看help/install
- 初次使用需要注册用户（之后会加入用户权限控制）

## 资产管理
### 1、添加主机
**单台主机添加，需要填写主机的全部信息，一次只能添加一台**  
![](http://i.imgur.com/QoPa8ze.png)
**批量添加主机，切记不用填写主机的全部信息，只需写ip 主机名即可，写多会报错（下个版本会增加判断用户的输入）**  
![](http://i.imgur.com/dr4SPXC.png)  
![](http://i.imgur.com/jtXDNbv.png)
**提交后，会提示提交成功的有几个，如果重复多次提交，就会提示有几台服务器已存在**

### 2、主机列表
**资产管理==>>主机列表**  
![](http://i.imgur.com/CB5JFWZ.png)  

1. **更新：点击绿色更新按钮，然后鼠标放到主机名的位置，就会显示服务器的基本信息，第一次不点击更新不会显示，每次点击都会重新获取，如服务器可变化的参数：内存等等，如下图：** 
![](http://i.imgur.com/jTpGORn.png) 
2. **编辑：点击编辑按钮，可以修改服务器的信息，这里以数据库的ID为主键，所以IP也可以修改，可以理解为原来的删除又重新创建，但是主键ID不改变，如下图：**  
![](http://i.imgur.com/FI3tSih.png)  
3. **删除：点击删除按钮，此服务器就会被删除，需要注意的是，在密钥管理菜单中也有主机列表，那个主机列表的删除仅仅是删除服务器上的所有公钥，不会删除服务器，如下图：**  
![](http://i.imgur.com/oKIRIlk.png)  

## 密钥管理
### 1、密钥用户
**以用户为入口，可以增加密钥用户，修改用户公钥，对某用户授权其可以登陆的服务器**  
**增加密钥用户：填写用户名，公钥（公钥格式要填写正确，否则无法推送）**
![](http://i.imgur.com/B7mA92i.png)  
![](http://i.imgur.com/CalhJM3.png)  

1. **编辑：点击编辑，弹出一个主机列表，可以对主机列表的服务器给此用户授权，主机列表的服务器就是资产管理中添加的主机，如下图：**  
![](http://i.imgur.com/BGMqy1d.png)  
**添加成功后，鼠标点击可登陆的服务器数即能显示此用户可以登陆的服务器，如果不看，需要再点击一次，多台服务器的话都可以点出来，一起看，如下图：**  
![](http://i.imgur.com/tctIbIG.png)

2. **删除：删除会删除此用户的所有的授权信息，并把此用户的可登陆的服务器的公钥都删除，但不会删除用户本身，之后的版本会加入离职人员，删除授权信息加用户本身，如下图：**  
![](http://i.imgur.com/lzB8715.png)  
![](http://i.imgur.com/04kfMAi.png)  
3. **更新公钥：可以对此用户的公钥修改更新，如下图：**  
![](http://i.imgur.com/mC0McnZ.png)  
### 2、主机列表
**以主机为入口，可以对服务器进行用户授权，删除权限**  
![](http://i.imgur.com/2vAdfgu.png)  

1. **编辑：编辑显示用户列表，表示对此服务器可以允许哪些用户登录，如下图：**  
![](http://i.imgur.com/5zbhdos.png)  

**授权成功后，点击允许登陆的用户，即可显示此服务器允许登陆的用户名，如下图**  
![](http://i.imgur.com/K563CUC.png)
2. **删除：只删除此服务器的所有公钥信息，不能删除服务器，如需删除服务器请到资产管理==>>主机列表中的删除**