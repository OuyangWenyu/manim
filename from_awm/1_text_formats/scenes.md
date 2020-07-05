# Text format

程序首先要导入相应的包。

```python3
from manimlib.imports import *
```

## Programs

第一个类是一个简单的书写类。在根目录下先执行：

```Shell
python manim.py from_awm/1_text_formats/text_formats.py -pl
```

可以看到命令行里询问执行哪个类，WriteText 是第21个，因此，这里输入21，然后敲回车即可。

稍微解释下这里的代码，construct是需要override的函数，通过TextMobject可以创建一个文本对象，
Write类会把文本做成动画，动画形式是“从左到右像手写出来一样”，然后通过play的形式播放。

还有别的动画类，比如 GrowFromCenter，FadeIn 等，和powerpoint中的动画形式类似。

```python3
class WriteText(Scene): 
    def construct(self): 
        text = TextMobject("This is a regular text")
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/WriteText.gif" /></p>

相比之下，AddText里用add就是直接把文字放到画板上。

```python3
class AddText(Scene): 
    def construct(self): 
        text = TextMobject("This is a regular text")
        self.add(text)
        self.wait(3)
```

<p align="center"><img src ="gifs/AddText.gif" /></p>



```python3
class Formula(Scene): 
    def construct(self): 
        formula = TexMobject("This is a formula")
        self.play(Write(formula))
        self.wait(3)
```

<p align="center"><img src ="gifs/Formula.gif" /></p>

```python3
class TypesOfText(Scene): 
    def construct(self): 
        typesOfText = TextMobject("""
            This is a regular text,
            $this is a formula$,
            $$this is a formula$$
            """)
        self.play(Write(typesOfText))
        self.wait(3)
```

<p align="center"><img src ="gifs/TipesOfText.gif" /></p>

```python3
class TypesOfText2(Scene): 
    def construct(self): 
        typesOfText = TextMobject("""
            This is a regular text,
            $\\frac{x}{y}$,
            $$x^2+y^2=a^2$$
            """)
        self.play(Write(typesOfText))
        self.wait(3)
```

<p align="center"><img src ="gifs/TipesOfText2.gif" /></p>

```python3
class DisplayFormula(Scene): 
    def construct(self): 
        typesOfText = TextMobject("""
            This is a regular text,
            $\\displaystyle\\frac{x}{y}$,
            $$x^2+y^2=a^2$$
            """)
        self.play(Write(typesOfText))
        self.wait(3)
```

<p align="center"><img src ="gifs/DisplayFormula.gif" /></p>

```python3
class TextInCenter(Scene):
    def construct(self):
        text = TextMobject("Text")
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/TextInCenter.gif" /></p>

```python3
class TextOnTopEdge(Scene):
    def construct(self):
        text = TextMobject("Text")
        text.to_edge(UP)
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/TextOnTopEdge.gif" /></p>

```python3
class TextOnBottomEdge(Scene):
    def construct(self):
        text = TextMobject("Text")
        text.to_edge(DOWN)
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/TextOnBottomEdge.gif" /></p>

```python3
class TextOnRightEdge(Scene):
    def construct(self):
        text = TextMobject("Text")
        text.to_edge(RIGHT)
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/TextOnRightEdge.gif" /></p>

```python3
class TextOnLeftEdge(Scene):
    def construct(self):
        text = TextMobject("Text")
        text.to_edge(LEFT)
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/TextOnLeftEdge.gif" /></p>

```python3
class TextInUpperRightCorner(Scene):
    def construct(self):
        text = TextMobject("Text")
        text.to_edge(UP+RIGHT)
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/TextInUpperRightCorner.gif" /></p>

```python3
class TextInLowerLeftCorner(Scene): 
    def construct(self): 
        text = TextMobject("Text") 
        text.to_edge(LEFT+DOWN)
        self.play(Write(text))
        self.wait(3)
```

<p align="center"><img src ="gifs/TextInLowerLeftCorner.gif" /></p>

```python3
class CustomPosition1(Scene):
    def construct(self):
        textM = TextMobject("Text")
        textC = TextMobject("Central text")
        textM.move_to(0.25*UP) 
        self.play(Write(textM),Write(textC))
        self.wait(3)
```

<p align="center"><img src ="gifs/CustomPosition1.gif" /></p>

```python3
class CustomPosition2(Scene):
    def construct(self):
        textM = TextMobject("Text")
        textC = TextMobject("Central text")
        textM.move_to(1*UP+1*RIGHT)
        self.play(Write(textM),Write(textC))
        self.wait(1)
        textM.move_to(1*UP+1*RIGHT) 
        self.play(Write(textM))
        self.wait(3)
```

<p align="center"><img src ="gifs/CustomPosition2.gif" /></p>

```python3
class RelativePosition1(Scene):
    def construct(self):
        textM = TextMobject("Text")
        textC = TextMobject("Reference text")
        textM.next_to(textC,LEFT,buff=1) 
        self.play(Write(textM),Write(textC))
        self.wait(3)
```

<p align="center"><img src ="gifs/RelativePosition1.gif" /></p>

```python3
class RelativePosition2(Scene):
    def construct(self):
        textM = TextMobject("Text")
        textC = TextMobject("Reference text")
        textM.shift(UP*0.1)
        self.play(Write(textM),Write(textC))
        self.wait(3)
```

<p align="center"><img src ="gifs/RelativePosition2.gif" /></p>

```python3
class RotateObject(Scene):
    def construct(self):
        textM = TextMobject("Text")
        textC = TextMobject("Reference text")
        textM.shift(UP)
        textM.rotate(PI/4) # <- Radians
        # You can use .rotate(45*DEGREES) too
        self.play(Write(textM),Write(textC))
        self.wait(2)
        textM.rotate(PI/4)
        self.wait(2)
        textM.rotate(PI/4)
        self.wait(2)
        textM.rotate(PI/4)
        self.wait(2)
        textM.rotate(PI)
        self.wait(2)
```

<p align="center"><img src ="gifs/RotateObject.gif" /></p>

```python3
class FlipObject(Scene):
    def construct(self):
        textM = TextMobject("Text")
        textM.flip(UP)
        self.play(Write(textM))
        self.wait(2)
```

<p align="center"><img src ="gifs/MirrorObject.gif" /></p>

```python3
class SizeTextOnLaTeX(Scene):
    def construct(self):
        textHuge = TextMobject("{\\Huge Huge Text 012.\\#!?} Text")
        texthuge = TextMobject("{\\huge huge Text 012.\\#!?} Text")
        textLARGE = TextMobject("{\\LARGE LARGE Text 012.\\#!?} Text")
        textLarge = TextMobject("{\\Large Large Text 012.\\#!?} Text")
        textlarge = TextMobject("{\\large large Text 012.\\#!?} Text")
        textNormal = TextMobject("{\\normalsize normal Text 012.\\#!?} Text")
        textsmall = TextMobject("{\\small small Text 012.\\#!?} Texto normal")
        textfootnotesize = TextMobject("{\\footnotesize footnotesize Text 012.\\#!?} Text")
        textscriptsize = TextMobject("{\\scriptsize scriptsize Text 012.\\#!?} Text")
        texttiny = TextMobject("{\\tiny tiny Texto 012.\\#!?} Text normal")
        textHuge.to_edge(UP)
        texthuge.next_to(textHuge,DOWN,buff=0.1)
        textLARGE.next_to(texthuge,DOWN,buff=0.1)
        textLarge.next_to(textLARGE,DOWN,buff=0.1)
        textlarge.next_to(textLarge,DOWN,buff=0.1)
        textNormal.next_to(textlarge,DOWN,buff=0.1)
        textsmall.next_to(textNormal,DOWN,buff=0.1)
        textfootnotesize.next_to(textsmall,DOWN,buff=0.1)
        textscriptsize.next_to(textfootnotesize,DOWN,buff=0.1)
        texttiny.next_to(textscriptsize,DOWN,buff=0.1)
        self.add(textHuge,texthuge,textLARGE,textLarge,textlarge,textNormal,textsmall,textfootnotesize,textscriptsize,texttiny)
        self.wait(3)
```

<p align="center"><img src ="gifs/SizeTextOnLaTeX.gif" /></p>

```python3
class TextFonts(Scene):
    def construct(self):
        textNormal = TextMobject("\\textrm{Roman serif text 012.\\#!?} Text")
        textItalic = TextMobject("\\textit{Italic text 012.\\#!?} Text")
        textTypewriter = TextMobject("\\texttt{Typewritter text 012.\\#!?} Text")
        textBold = TextMobject("\\textbf{Bold text 012.\\#!?} Text")
        textSL = TextMobject("\\textsl{Slanted text 012.\\#!?} Text")
        textSC = TextMobject("\\textsc{Small caps text 012.\\#!?} Text")
        textNormal.to_edge(UP)
        textItalic.next_to(textNormal,DOWN,buff=.5)
        textTypewriter.next_to(textItalic,DOWN,buff=.5)
        textBold.next_to(textTypewriter,DOWN,buff=.5)
        textSL.next_to(textBold,DOWN,buff=.5)
        textSC.next_to(textSL,DOWN,buff=.5)
        self.add(textNormal,textItalic,textTypewriter,textBold,textSL,textSC)
        self.wait(3)
```
<p align="center"><img src ="gifs/TextFonts.gif" /></p>
