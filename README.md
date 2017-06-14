
# [CentOS](/OS/CentOS)
# [Vim](/Vim/vim)

# Go Lang
## godoc
````
export GOPATH=/usr/lib/golang
godoc -http=:6060
````

# Install TrueType Font in Linux
````
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
````
