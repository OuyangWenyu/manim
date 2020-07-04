# Manim中文简介

这是一个很强大的数学相关的可视化软件，科研搞不动的时候可以把玩一下。本项目从[manim github](https://github.com/3b1b/manim) fork而来，
并另外参考了：[Manim教程合集](https://www.bilibili.com/video/BV1W4411Z7Zt?from=search&seid=5908821040753595740)，[Elteoremadebeethoven/AnimationsWithManim](https://github.com/Elteoremadebeethoven/AnimationsWithManim) 等来补充自己的内容。

## manim是什么

准确地说，manim是一个动画制作软件，是由Grant Sanderson制作的，他就是3blue1brown。manim主要由5个部分组成，

- Python：核心程序
- LATEX：处理文本公式
- Cairo：制作图片
- FFmpeg：图片渲染合集成视频
- SoX：处理音频

## Windows下的安装

平常日用电脑还是以windows为主，所以本系列实践还是在windows上开展。这里直接使用conda来安装，按照manim项目介绍只需要安装LATEX和SoX。

首先，安装LATEX相关软件。根据[官网](https://www.latex-project.org/get/)介绍，LATEX有几种不同的版本，在windows下的推荐是MikTeX，proTeXt或者Tex Live，三者中好像只有Tex Live是跨平台的，因此，这里暂时就选择它了。TeX Live网站：http://www.tug.org/texlive/ ，文档：http://www.tug.org/texlive/doc.html

首先，获取TeX Live：http://www.tug.org/texlive/acquire.html ，文档推荐的方式是在线安装，那就在线吧：http://www.tug.org/texlive/acquire-netinstall.html

下载windows下的exe包。点击运行。可能提示不安全，不要紧，可以允许。然后接下来按照提示依次执行下去即可。然后会弹出一个GUI的安装窗口。我就直接默认安装了。因为这是个在线安装，应该是边下载边安装的，所以整个安装过程还是比较耗时的，耐心等待即可，在这期间可以继续下面的安装。

接下来安装SoX。去到下载网站：https://sourceforge.net/projects/sox/files/sox/ ，貌似只有32位的，先尝试下了。点击安装即可。我仍然选择默认安装。同样需要将其添加到环境变量中，我的路径是：C:\Program Files (x86)\sox-14-4-2

然后接下来安装miniconda或anaconda，这部分可以参考：https://github.com/OuyangWenyu/hydrus/blob/master/1-basic-envir/2-python-envir.ipynb

然后clone本项目并在本项目根目录下打开命令行执行：

```Shell
conda env create -f environment.yml
```

这样就安装好manim环境了，接下来可以尝试运行下示例代码。个人使用了pycharm作为IDE，因此就用PyCharm打开该项目即可，然后配置python解释器到manim环境下。

## 基本使用

按照项目给的例子，在项目根目录下打开cmd，执行：

```Shell
python -m manim example_scenes.py SquareToCircle -pl
```

简单解释下这个命令。

“python”的意思是用python来执行，-m manim 等价于 manim.py，即执行这个python文件。

manim.py 是本项目程序的启动代码，需要给它另一个文件作为其运行参数，这个文件是具体要执行的场景。
这里的例子就是 example_scenes.py。

打开example_scenes.py 可以看到里面定义了很多类，每个类都继承了Scene父类，这些类定义了画面的具体内容，更多细节以后再记录。

然后SquareToCircle 就是具体执行哪个 Scene子类，-pl表示的是 preview in low quality，也就是说低码质量来查看，这样可以更快地预览自己的代码效果。

按照前面的步骤之后，发现并不能成功运行，提示还需要安装一些module，那么就继续安装一下。

首先，报错提示的是没有 pygments，所以网上搜索，用下面命令安装：

```Shell
pip install Pygments
```

然后我这里就能运行了，程序生成视频后会调用默认的播放器，这里我使用的是potplayer。

接下来就试试其他几个Scene子类。

```Shell
python -m manim example_scenes.py OpeningManimExample -pl
python -m manim example_scenes.py WarpSquare -pl
python -m manim example_scenes.py WriteStuff -pl
python -m manim example_scenes.py UpdatersExample -pl
```

通过命令行里执行的结果，可以看到制作的视频都保存在了media\videos\example_scenes 文件夹下，因为这里使用的都是-pl，所以都在 \480p15 子文件夹里。

## 基础示例之AnimationsWithManim

接下来就可以进入正式实践了，例子以[Elteoremadebeethoven/AnimationsWithManim](https://github.com/Elteoremadebeethoven/AnimationsWithManim)的程序为主，
更多视频介绍可以参考：[Manim教程合集](https://www.bilibili.com/video/BV1W4411Z7Zt?from=search&seid=5908821040753595740)。

下载 AnimationsWithManim 的代码，这里就不git clone了，直接下载zip文件，并解压。在本项目根目录下新建文件夹：from_awm，
然后把用的到的AnimationsWithManim的文件放入from_awm文件夹中，我这里已经放好了，就不一一说了。

更多内容详见from_awm 文件夹下的例子。
