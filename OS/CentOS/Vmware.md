# Compile vmware tools
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

## See Also
* Reference [Centos 7.3安裝vmtools](http://www.cnblogs.com/chenfool/p/6808245.html)

# GUI Window is disappeared
When we show down the vmware by force, GUI window will be disappeared. After the logo of CentOS, the blank screen will appear, but, where is my login window?

There is no method to recovery from this disaster when I look up in www. I have to try to solve it by self.

I use `Ctrl+Alt+2` to login terminal and run `starx`, the GUI window come back. It means my system can work on XWindow. I can use this method to login but it is not easy. I must find the other method.

I `cat /etc/inittab' in order to view runlevel. But in CentOS 7, the /etc/inittab has been changed to 
```bash
# inittab is no longer used when using systemd.
#
# ADDING CONFIGURATION HERE WILL HAVE NO EFFECT ON YOUR SYSTEM.
#
# Ctrl-Alt-Delete is handled by /usr/lib/systemd/system/ctrl-alt-del.target
#
# systemd uses 'targets' instead of runlevels. By default, there are two main targets:
#
# multi-user.target: analogous to runlevel 3
# graphical.target: analogous to runlevel 5
#
# To view current default target, run:
# systemctl get-default
#
# To set a default target, run:
# systemctl set-default TARGET.target
#
```
Oh, there is no runlevel setting here. What is targets? I run `systemctl get-default`, it shows `graphical.target`. It should be work but now it does not. I have to do the following as root
```bash
# change default target to multi-user.target
systemctl set-default multi-user.target
# reboot 
reboot
```
Ok, it login in terminal directly. And I run the following as root again
```bash
# change default target to graphical.target
systemctl set-default graphical.target
# reboot 
reboot
```
My GUI window come back!

[Back to Home](https://husthed.github.io) | [CentOS](/OS/CentOS)
