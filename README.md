# Blockcast节点设置教程
![image](https://github.com/user-attachments/assets/ae2acd06-9869-4d23-880b-ba4caad8cf71)

## 你需要准备的东西
* CPU>2和内存大于500M以上的VPS
* 一个电子邮箱或者谷歌账户
* 推特账户和Discord账户以及一个SOL钱包(无需私钥仅用于社交绑定)
* 系统我选择ubuntu

## 节点教程开始
### 更新系统apt索引包
```
sudo apt-get update
```
### 安装APT依赖包
```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
### 添加 Docker 的官方 GPG 密钥
```
curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```
### 设置稳定版仓库
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/ \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
### 安装最新版本的 Docker Engine-Community 和 containerd、compose
```
sudo apt-get update
```
```
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```
### 重启Docker
```
sudo systemctl enable docker
```
```
sudo systemctl start docker
```
### 查看Docker版本
```
docker --version
```
```
docker compose version
```
### 获取Blockcast节点文件
```
git clone https://github.com/Blockcast/beacon-docker-compose.git
```
```
cd beacon-docker-compose
```
### 使用compose运行节点
```
docker-compose up -d
```
### 查看是否运行成功
```
docker ps
```
运行成功要有4个容器，如图所示

![image](https://github.com/user-attachments/assets/44706739-ce86-48cd-b3de-da990fbd659e)

### 获取Hardware ID和Challenge Key
```
docker-compose exec blockcastd blockcastd init
```
一定要保存好这两个数据
### 注册账号及绑定社交帐号
* 打开链接注册账号：[Blockcast](https://app.blockcast.network?referral-code=RWXaU1)
* 可以使用邮箱注册或者直接使用谷歌注册
* 注册成功之后点击右上角的Profile按钮，绑定sol钱包、推特账户、Discord账户
* 返回主页完成任务可以获得奖励积分

![image](https://github.com/user-attachments/assets/bbf56e3b-222c-4046-ba28-c24e9b735f75)
### 绑定节点
点击Manage Nodes，再点击Register Node，会弹出绑定节点的界面，输入你的节点Hardware ID和Challenge Key

![image](https://github.com/user-attachments/assets/06de8583-bc23-453e-b7bf-ab8b5df75b48)

![image](https://github.com/user-attachments/assets/878648df-973f-4804-82fc-30d5fea9302f)

位置这里输入你vps所在的位置，仅需要国家就行，例如你的vps是德国的，你就输入中文德国，下面会出现选项，选择德国就行

注册完成之后等待大概5-10分钟，没有问题的话你的节点就会显示上线，并在主页面显示你的节点每小时能获得的积分

![image](https://github.com/user-attachments/assets/ca7d9222-04fd-4be4-8646-598509e11fff)

节点必须在线6小时以上才会进行连通性测试，连续24小时在线后才会开始发放积分奖励





