# Install Jekyll

However, the modern approach in many circumstances, including in development, is to use a tool that lets you easily install and use Ruby as a normal user. This lets you avoid having to become root. There are a few such tools, and the one I use is RVM.

install rvm into your ~ (may need restart terminal)
```
\curl -sSL https://get.rvm.io | bash -s stable
```

install latest version of ruby into your ~
```
rvm install ruby
```

installs a gem into your ~
```
gem install $SOME_GEM_NAME
```
```
gem install jekyll bundler
```

**Install Ruby**

To install the latest version of Ruby, run:
```
rvm install ruby
rvm --default use ruby
```

To install a specific version of Ruby, run:
```
rvm install ruby-X.X.X
rvm --default use ruby-X.X.X
```

and then
```
bundle install
jekyll serve
```
should work

## Jekyll Blog

https://jekyllrb.com/docs/usage/ 
https://www.jekyll.com.cn/docs/usage/ 
初始准备
gem install jekyll bundler
jekyll new blog
cd blog
bundle exec jekyll serve
bundle install

基本使用
jekyll build
# => The current folder will be generated into ./_site
jekyll build --watch
# => The current folder will be generated into ./_site,
#    watched for changes, and regenerated automatically.
built-in development server 
jekyll serve
# => A development server will run at http://localhost:4000/
# Auto-regeneration: enabled. Use `--no-watch` to disable.

jekyll serve --livereload
# LiveReload refreshes your browser after a change.

How to add plugins
jekyll-watch 
url: https://github.com/jekyll/jekyll-watch
介绍
Rebuild your Jekyll site when a file changes with the --watch switch.

进入博客文件夹
```
Add this line to your application's Gemfile:
gem 'jekyll-watch'
And then execute:
bundle

Option: or install it yourself as:
gem install jekyll-watch

Remove jekyll-watch
sudo gem uninstall jekyll-watch
```

如何使用
Pass the --watch flag to jekyll build or jekyll serve:
```
jekyll build --watch
jekyll serve --watch
```
添加自定义域名
这个部分分两种情况，第一种情况就是只是 添加自定义的域名；第二种情况就是添加自定义域名之后，并 通过 https 访问。
第一种情况，当你已经申请好了自定义的域名之后
第一步，建立 CNAME 文件
在博客所在的根目录建立  CNAME 文件，并且把自定义的域名写入其中。如下图

第二步，需要到 DNS 配置中添加三条记录
```
@          A             192.30.252.153
@          A             192.30.252.154
www      CNAME           username.github.io
用你自己的 Github 用户名替换 username。
```

这里的 DNS 配置添加，可以在你购买域名的服务商处设置，如 godaddy，阿里云。也可以在 DNS 服务商那里设置，如 cloudflare，DNSPOD。
第三步，等待你的 DNS 配置生效
对DNS的配置不是立即生效的，过10分钟再去访问你的域名看看有没有配置成功 : )D
第二种情况，添加 https
首先为什么要加 https，关于这个问题可以参考知乎 为什么 2015 年底各大网站都纷纷用起了 HTTPS？

当你已经完成第一种情况的部署了，接下来要做的是
去你的域名注册商更改 dns server 成 cloudflare 所提供的
在 cloudflare 设置 A record 
在 cloudflare 配置 crypto ，选择 flexiable （这一步要一段时间才能起效）
在 cloudflare 配置 page rule ，一个是 always use https ，一个是 redirect http 到 https 每一步的操作可能需要 5-30 分钟才能起效
首先为什么使用Cloudflare提供的免费SSL
收费的SSL服务总是比免费的更加周到，一般收费的SSL都会提供端到端的加密。但是价格不菲，对于个人博客来说，这是一笔不必要的开销。我只是需要看到网站地址栏有绿色的锁头，那就证明我们的网站相对安全了。

此外，使用https之后，谷歌、百度等搜索排名权值（PR等）也会有相对提升。
还有其他的一些，例如Cloudflare还提供免费的CDN和缓存技术，让浏览者有更好的体验
创建CloudFlare帐户，并添加网站
如果你还没有Cloudflare账号，点击注册
登陆后，点击这里 增加你的域名，如下图，输入你的域名，例如 sayidhe.com 并点击 Add Site.


点击 Confirm Plan


这一部分就是从 DNS 设置哪里拉去过来的 DNS 配置，选择 Continue


接下来这一步比较关键，要去 域名购买商 那里把 Nameservers 改成，cloudflare 的，下图右边部分。这里 阿里云 是不允许国外的 Nameserver。

所以我以 godaddy 为例子。DNS 设置下方有 Nameservers，把它改成 Costom，然后填入 Cloudflare 提供的 nameservers 就可以了。 

注：官方说明，域名服务器修改最长需要72小时生效 ，用了两个域名测试，大约需要 5~30 分钟，看到 Status: Active 即可
、
设置SSL
点击 crypto 菜单 , 然后设置 Flexible SSL ，如下图


设置 Page rules，设置 always Use HTTPS




至此，设置完成。一般需要5~30分钟生效！！！可能需要重新断开网络连接。效果如下，加了一把小锁。


参考
Add HTTPS/SSL to Github pages for custom domain Free
Set Up SSL on Github Pages With Custom Domains for Free

微信文章分享
微信分享链接的缩略图

微信内分享
在微信内打开链接后，点右上角【…】选择【发送给朋友】或【分享到朋友圈】，这种分享方式获取缩略图的方法：

方法一：在页面 body 最上方添加 300*300 像素的 img
如该图片不需要显示，可以用 css 隐藏，但不能直接对 img 设置 display: none;。
可以在父层 div 上设置 display: none; 或者对 img 设置 position: absolute; visibility: hidden;。
<div style="display:none;"><img src="/img/thumbnail.png" alt=""></div>
方法二：通过微信 JS-SDK 的分享接口
这种方法需要一个微信公众号的 app_id，同时需要一个后端服务生成 signature。好处是可以定制分享的标题、缩略图、描述。

可参看澎湃新闻的分享实现方式。
从浏览器分享
在浏览器打开链接后，点分享图标，选择【微信】，这种分享方式获取缩略图的方法：
在页面的 head 部分添加 Open Graph Metadata：
<meta property="og:type" content="website" />
<meta property="og:title" content="页面标题">
<meta property="og:description" content="页面描述">
<meta property="og:image" content="http://www.example.com/img/thumbnail.png">
<meta property="og:url" content="http://www.example.com/">
其中 og:image 影响浏览器分享时的图标，需要指定图片的完整路径。
Header  设置
语言设置
Declaring language in HTML
HTTP headers, meta elements and language information

GA
https://desiredpersona.com/google-analytics-jekyll/
优化
Jekyll Highlighter
Supported language highlighters in Pygments for Jekyll and GitHub Pages: https://haisum.github.io/2014/11/07/jekyll-pygments-supported-highlighters/

https://www.jianshu.com/p/12badb7e6c10 
https://www.jianshu.com/p/3fc93c16ad2d


添加 RSS

https://github.com/jekyll/jekyll-feed
注意
Jekyll：解决Auto-regeneration can no longer be set from your configuration file(s)
运行 jekyll serve 在本地运行jekyll网站的时候出现该问题：
Deprecation: Auto-regeneration can no longer be set from your configuration file(s). Use the –[no-]watch/-w command-line option instead.
解决方法
删除_config.yml文件中的 auto: true 语句


以下为在 Ubuntu 中

Use Commands

/*Share With Mac*/
sudo mount -t vboxsf For_Share /mnt/SharedPoint/
sudo adduser $USER vboxsf

/*Start*/
sudo apt install ruby
sudo apt-get install ruby-dev
sudo gem install jekyll

/*Install git - Need VPN*/
sudo apt install git
sudo apt install ruby-bundler
bundle install

/*npm install*/
sudo apt install nodejs-legacy
npm install
npm start

/*gulp install*/
npm install -g gulp
npm install --save-dev gulp
npm rebuild node-sass

/*Build - Delete old Gemfile.lock first*/
cd sayidly.github.io/
bundle exec jekyll build
bundle exec jekyll serve
gulp

/*Push to GitHub*/
git add .
git commit -m "Delete something"
git push -f origin master
git config --local -e
git checkout --orphan gh-pages
git rm -rf .
echo "My Page" > index.html
git add index.html
git commit -a -m "First pages commit"
git push origin gh-pages



