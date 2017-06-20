
# [CentOS](/OS/CentOS)
# [Vim](/Vim/vim)

# Go Lang
## godoc
```bash
export GOPATH=/usr/lib/golang
godoc -http=:6060
```

# Install TrueType Font in Linux
```bash
# Example of YaHei Consolas Hybrid 
mkdir /usr/share/fonts/truetype/Yahei
cp yahei*.ttf /usr/share/fonts/truetype/Yahei
cd /usr/share/fonts/truetype/Yahei
# 创建字体的fonts.scale文件，它用来控制字体旋转缩放
sudo mkfontscale
# 创建字体的fonts.dir文件，它用来控制字体粗斜体产生
sudo mkfontdir
# 建立字体缓存信息，也就是让系统认识该字体
sudo fc-cache -fv
```

# Work with GitHub at Local
* Create a GitHub account
* Generate ssh key at local
```bash
ssh-keygen -t rsa -C "your_email@youremail.com"
```
here your_emaie is your email address.
* Add SSH keys in GitHub
    * Choose Account Settings->SSH Keys
    * Choose Add SSH Key, filled a tile and paste your public key
* Test
```bash
ssh -T git@github.com
```
If 
```
The authenticity of host 'github.com (192.30.255.113)' can't be established.
RSA key fingerprint is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,192.30.255.113' (RSA) to the list of known hosts.
Hi YYYYYY! You've successfully authenticated, but GitHub does not provide shell access.
```
now you can connect with Github.
* Config
```bash
git config --global user.name "your_name"
git config --global user.email "your_email"
```
* Clone

Using `Copy to clipboard` in `Clone or Download` of repository to copy git address
```bash 
git clone git_address
```
* Commit
