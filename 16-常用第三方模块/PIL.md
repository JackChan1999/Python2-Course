PIL：Python Imaging Library，已经是Python平台事实上的图像处理标准库了。PIL功能非常强大，但API却非常简单易用。

### 安装PIL

在Debian/Ubuntu Linux下直接通过apt安装：

```
$ sudo apt-get install python-imaging

```

Mac和其他版本的Linux可以直接使用easy_install或pip安装，安装前需要把编译环境装好：

```
$ sudo easy_install PIL

```

如果安装失败，根据提示先把缺失的包（比如openjpeg）装上。

Windows平台就去[PIL官方网站](http://pythonware.com/products/pil/)下载exe安装包。

### 操作图像

来看看最常见的图像缩放操作，只需三四行代码：

```
import Image

# 打开一个jpg图像文件，注意路径要改成你自己的:
im = Image.open('/Users/michael/test.jpg')
# 获得图像尺寸:
w, h = im.size
# 缩放到50%:
im.thumbnail((w//2, h//2))
# 把缩放后的图像用jpeg格式保存:
im.save('/Users/michael/thumbnail.jpg', 'jpeg')

```

其他功能如切片、旋转、滤镜、输出文字、调色板等一应俱全。

比如，模糊效果也只需几行代码：

```
import Image, ImageFilter

im = Image.open('/Users/michael/test.jpg')
im2 = im.filter(ImageFilter.BLUR)
im2.save('/Users/michael/blur.jpg', 'jpeg')

```

效果如下：

![PIL-blur](http://www.liaoxuefeng.com/files/attachments/001407671964310a6b503be6fcb4648928e2e4c522d04c7000)

PIL的`ImageDraw`提供了一系列绘图方法，让我们可以直接绘图。比如要生成字母验证码图片：

```
import Image, ImageDraw, ImageFont, ImageFilter
import random

# 随机字母:
def rndChar():
    return chr(random.randint(65, 90))

# 随机颜色1:
def rndColor():
    return (random.randint(64, 255), random.randint(64, 255), random.randint(64, 255))

# 随机颜色2:
def rndColor2():
    return (random.randint(32, 127), random.randint(32, 127), random.randint(32, 127))

# 240 x 60:
width = 60 * 4
height = 60
image = Image.new('RGB', (width, height), (255, 255, 255))
# 创建Font对象:
font = ImageFont.truetype('Arial.ttf', 36)
# 创建Draw对象:
draw = ImageDraw.Draw(image)
# 填充每个像素:
for x in range(width):
    for y in range(height):
        draw.point((x, y), fill=rndColor())
# 输出文字:
for t in range(4):
    draw.text((60 * t + 10, 10), rndChar(), font=font, fill=rndColor2())
# 模糊:
image = image.filter(ImageFilter.BLUR)
image.save('code.jpg', 'jpeg');

```

我们用随机颜色填充背景，再画上文字，最后对图像进行模糊，得到验证码图片如下：

![验证码](http://www.liaoxuefeng.com/files/attachments/0014076720724832de067ce843d41c58f2af067d1e0720f000)

如果运行的时候报错：

```
IOError: cannot open resource

```

这是因为PIL无法定位到字体文件的位置，可以根据操作系统提供绝对路径，比如：

```
'/Library/Fonts/Arial.ttf'

```

要详细了解PIL的强大功能，请请参考PIL官方文档：

[http://effbot.org/imagingbook/](http://effbot.org/imagingbook/)