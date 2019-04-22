---
layout:     post
title:      "Vue Learning"
subtitle:   " \"Vue learning\""
date:       2019-04-22 18:23:00
author:     "王琼弟"
catalog: true
tags:
    - 前端
    - Vue
---

转载自[简书](https://www.jianshu.com/p/88b1ca600f4f)

#### 下载node.js和git

下载链接:[node.js](https://nodejs.org/en/download/),[git](https://git-scm.com/downloads)。

我们先认识一下npm。

npm是什么东东？npm其实是Node.js的包管理工具（package manager）。

为啥我们需要一个包管理工具呢？因为我们在Node.js上开发时，会用到很多别人写的JavaScript代码。如果我们要使用别人写的某个包，每次都根据名称搜索一下官方网站，下载代码，解压，再使用，非常繁琐。于是一个集中管理的工具应运而生：大家都把自己开发的模块打包后放到npm官网上，如果要使用，直接通过npm安装就可以直接用，不用管代码存在哪，应该从哪下载。

更重要的是，如果我们要使用模块A，而模块A又依赖于模块B，模块B又依赖于模块X和模块Y，npm可以根据依赖关系，把所有依赖的包都下载下来并管理起来。否则，靠我们自己手动管理，肯定既麻烦又容易出错。

讲了这么多，npm究竟在哪？

其实npm已经在Node.js安装的时候顺带装好了。（copy from [liaoxuefeng](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/00143450141843488beddae2a1044cab5acb5125baf0882000))

验证一下安装是否成功。打开cmd，输入`node -v`、`npm -v`和`git --version`

安装hexo