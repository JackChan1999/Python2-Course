## 使⽤ Beautiful Soup 解析数据

有的⼩伙伴们对写正则表达式的写法⽤得不熟练，没关系，我们还有⼀个更强⼤的⼯具，叫Beautiful Soup，有了它我们可以很⽅便地提取出HTML或XML标签中的内容，实在是⽅便，这⼀节就让我们⼀起来感受⼀下Beautiful Soup的魅⼒

### Beautiful Soup的简介

简单来说，Beautiful Soup是python的⼀个库，最主要的功能是从⽹⻚抓取数据。官⽅解释如下：

> Beautiful Soup提供⼀些简单的、python式的函数⽤来处理导航、搜索、修改分析树等功能。它是⼀个⼯具箱，通过解析⽂档为⽤户提供需要抓取的数据，因为简单，所以不需要多少代码就可以写出⼀个完整的应⽤程序。 Beautiful Soup⾃动将输⼊⽂档转换为Unicode编码，输出⽂档转换为utf-8编码。你不需要考虑编码⽅式，除⾮⽂档没有指定⼀个编码⽅式，这时，Beautiful Soup就不能⾃动识别编码⽅式了。然后，你仅仅需要说明⼀下原始编码⽅式就可以了。 Beautiful Soup已成为和lxml、html6lib⼀样出⾊的python解释器，为⽤户灵活地提供不同的解析策略或强劲的速度。

### 安装

下载地址: https://pypi.python.org/pypi/beautifulsoup4/4.3.2
官⽅⽂档： http://beautifulsoup.readthedocs.org/zh_CN/latest