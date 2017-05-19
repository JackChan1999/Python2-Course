## 提取HTML正文内容

思路：我把这里的正文理解为网页中我主要内容，那么怎么去抓取这个主要内容呢？我一开始的想法是用beautifulsoup来解析网页，但是又想到如果要抽取正文的话这样做还涉及到比较复杂的算法，而且对于不同的网页来说效果可能做不到很好。后来我发现了Pythongoose（Github）这个神器，它是基于NLTK和Beautiful Soup的，分别是文本处理和HTML解析的领导者，目标是给定任意资讯文章或者任意文章类的网页，不仅提取出文章的主体，同时提取出所有元信息以及图片等信息，支持中文网页（用到了结巴分词）。这个正好符合需求，所以直接拿来用了。

```python
#!/usr/bin/env python
#coding: utf-8
from goose import Goose
from goose.text import StopWordsChinese
import sys
reload(sys)
sys.setdefaultencoding("utf-8")

# 要分析的网页url
#url = 'http://c.itcast.cn/index.html'
url = 'https://linux.cn/article-6717-1.html'

def extract(url):
    '''
    提取网页正文
    '''
    g = Goose({'stopwords_class': StopWordsChinese})
    article = g.extract(url=url)
    return article.cleaned_text

if __name__ == '__main__':
    print extract(url)
```