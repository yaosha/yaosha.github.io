---
title: 内网Windows安装Jekyll
---

{% capture article %}
本文记录在华为内网Windows环境中安装Jekyll的流程。

## 安装Ruby

### 下载

- 下载地址：http://rubyinstaller.org/downloads/。
- 版本选择2.3.3因为内网镜像缺少最新的一些依赖包。
- 根据电脑64位或32位选择 如64位的Ruby 2.3.3 (x64)。

### 安装

1. 安装所有选项都勾选上以免出现未知情况，安装地址推荐C盘。
    ![Links](/images/docs/guides/jekyll/image001.png)
2. 右键Git Bash Here。
3. 输入 ruby –v 查看已经安装的ruby版本。

## 安装Ruby Development Kit
### 下载
- 下载地址：http://rubyinstaller.org/downloads/。
- 版本选择最新版本并根据电脑64位或32位选择。如64位的。

### 安装
1. 在Ruby Development Kit安装目录下 右键Git Bash Here。
2. ruby dk.rb init生成config.yml文件。
3. ruby dk.rb install 初始化。

### 安装FAQ
#### ruby dk.rb install 初始化报错
![Links](/images/docs/guides/jekyll/image003.png)

解决方法：
1. 编辑Ruby Development Kit安装目录下的config.yml文件末尾添加新的一行。
    例如：“- C:\Ruby200-x64” 。
    说明：一个杠加空格加ruby安装地址，记得不需要加bin目录。

2. 执行 dk.rb install。

## 增加华为gem镜像网站
方法：
1. 右键Git Bash Here。
2. 执行gem sources -a http://rnd-mirrors.huawei.com/rubygems/。
3. (可选)删除外网下载地址。gem resources --remove https://rubygems.org/

## 安装bundler & Jekyll
1. 执行gem install bundler。
2. 执行gem install jekyll。

## 新生成文件启动Jekyll服务
1. 在你想生成文件的文件夹下 右键Git Bash Here。
2. Jekyll new blog。
3. 在blog目录下右键Git Bash Here。
4. Jekyll serve。
5. 查看本地发布效果：直接访问localhost:4000。

### 新文件启动Jekyll FAQ
![Links](/images/docs/guides/jekyll/image005.png)

    解决方法：gem install minima
    
    
![Links](/images/docs/guides/jekyll/image007.png)

    解决方法： gem install Jekyll-feed
    
    
![Links](/images/docs/guides/jekyll/image009.png)

    解决方法：gem install tzinfo-data x64-mingw32
    
    

## 基于本地样机源文件启动Jekyll服务
1. 从github拷贝"https://github.com/yaosha/yaosha.github.io" 项目源代码到本地，注意本地路径不能包含中文否则发布时会出现异常。
2. 修改本地样机demo中的Gemfile文件。将第一行改为source "http://rnd-mirrors.huawei.com/rubygems/" ，把下载源路径切换为内网镜像地址。
3. 在样机demo文件夹下，右键Git Bash Here。
4. 输入命令bundler update，更新环境下的依赖包。
5. 手工下载jemoji文件。
    1. 下载网址https://rubygems.org/gems/jemoji。
    2. 单机网站右下角**download**。
    3. 下载并复制到Ruby安装目录。如：C:\Ruby23-x64\lib\ruby\gems\2.3.0\cache下。
6. 再次执行 bundler update。
7. 更新完后执行jekyll serve。
如果报错如下图所示：
   ![Links](/images/docs/guides/jekyll/image015.png)
   
执行命令启动服务：bundle exec jekyll serve。

{% endcapture %}

{% include templates/home.md %} 
  





