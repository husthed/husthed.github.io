**I don't want to search the same question one time by one time!** 
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
# 将修改提交到本地仓库
git config --global user.name "your_name"
# 将本地修改提交到github
git config --global user.email "your_email"
```
* Clone

Using `Copy to clipboard` in `Clone or Download` of repository to copy git address
```bash 
git clone git_address
```
* Commit

After some modifications, we need to commit it to github as following
```bash
git commit -m "your_message" your_modified_files
git push origin master
```
See Also
* [Linux下Git和Gitub使用方法总结](www.linuxidc.com/Linux/2014-03/97821.htm)
* [Linux下使用git命令及github项目](blog.csdn.net/five3/article/details/8904635)

# Centos 7 & Vmware Tools
When compiling the module of vmware tools, there is an error which result in "Share Directory" can't work. It is necessary to modify codes of vmware tools.

Let's do it now. First we need to open page.c.
```bash
cd $VM_TOOLS_DIR/lib/modules/source
tar xvf vmhgfs.tar
vim vmhgfs-only/page.c
```
And then modify the codes from
```c
1636 int
1637 HgfsWbRequestWait(HgfsWbPage *req)  // IN: request of page data to write
1638 {
1639 #if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 19, 0)
1640    return wait_on_bit_io(&req->wb_flags,
1641                          PG_BUSY,
1642                          TASK_UNINTERRUPTIBLE);
1643 #elif LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 13)
1644    return wait_on_bit(&req->wb_flags,
1645                       PG_BUSY,
1646 #if LINUX_VERSION_CODE < KERNEL_VERSION(3, 17, 0)
1647                       HgfsWbRequestWaitUninterruptible,
1648 #endif
1649                       TASK_UNINTERRUPTIBLE);
1650 #else
1651    wait_event(req->wb_queue,
1652               !test_bit(PG_BUSY, &req->wb_flags));
1653    return 0;
1654 #endif
1655 }
```
to (remove line 1646~1648)
```c
1636 int
1637 HgfsWbRequestWait(HgfsWbPage *req)  // IN: request of page data to write
1638 {
1639 #if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 19, 0)
1640    return wait_on_bit_io(&req->wb_flags,
1641                          PG_BUSY,
1642                          TASK_UNINTERRUPTIBLE);
1643 #elif LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 13)
1644    return wait_on_bit(&req->wb_flags,
1645                       PG_BUSY,
1646                       TASK_UNINTERRUPTIBLE);
1647 #else
1648    wait_event(req->wb_queue,
1649               !test_bit(PG_BUSY, &req->wb_flags));
1650    return 0;
1651 #endif
1652 }
```
And we retar the file and reinstall vmware tool.
```bash
tar cvf vmhgfg.tar vmhgfs-only
cd $VM_TOOLS_DIR/
./vmware-install.pl
```
All is ready now!
