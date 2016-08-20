# DisplayInfo
display info of device

####Download
<div align=center><img src="https://github.com/ZQiang94/DisplayInfo/blob/master/20160820231714.png"/></div><br/>

通过运行DisplayInfo获取当前设备屏幕的尺寸信息，运行效果如图（Honor 7）：
<img src="https://github.com/ZQiang94/DisplayInfo/blob/master/device-2016-08-20-115904.png" alt="dispalyinfo在Honor 7上的运行效果"><br/>
通过运行结果可以看出，华为Honor 7的屏幕尺寸（4.94约为5.0），分辨率（Resolution）为1080 * 1920（缺少的为下面的按键），DPI为480dpi等信息。另外还有一些
Android适配时需要了解的尺寸限定符，详细讲解见[官方文档对尺寸限定符的解释](https://developer.android.com/training/multiscreen/screensizes.html)。

####Des:<br/>
场景：切图是在1080 * 1920的图上进行标注，套图时该如何进行适配。<br/>
现在市场主流的两种分辨率类型（分别是1080 * 1920与720 * 1280）,具体的分布情况在下图中展示。
如图展示的为16年07月份分辨率市场分布情况：
[查看更详细信息(个推提供)](http://www.getui.com/data-report/equipment-info.html)<br/>
<img src="https://github.com/ZQiang94/DisplayInfo/blob/master/display_2016-8-20.png"/><br/>
下面是分辨率与对应基线的关系图<br/>
<img src="http://img.ui.cn/data/file/7/9/8/278897.png?imageView2/2/q/90"/><br/>
通过上图可以看出，场景中给出的在480dpi(1080 * 1920)的标注，要想适配480dpi的手机只需要将切图中的标注除以3即可（切图中的标注是px，需要转换成Android中的dp）。
想要使用480dpi的标注适配320dpi（720 * 1280），可以使用先将420dpi的设计图缩放成320dpi的设计图，借助ps可以实现。<br/>
<div align=center><img src="https://github.com/ZQiang94/DisplayInfo/blob/master/display_00.png"/><br/></div>
<img src="https://github.com/ZQiang94/DisplayInfo/blob/master/display_1080-720.png"/>
<img src="https://github.com/ZQiang94/DisplayInfo/blob/master/display_1920-1280.png"/><br/>
可以得出，1080 * 1920 缩放为720 * 1280时：<br/>
width：66.67%&emsp;&emsp;&emsp;height:79.01%<br/>
在使用设计图为480dpi(1080 * 1920)适配720 * 1280的时候先按照上述比例计算出720 * 1280的标注然后再除以2。


###基本概念
####1.屏幕尺寸：手机实际物理尺寸，一般用英寸来表示（1 英寸 = 2.54 厘米）。
手机尺寸计算方式=对角线尺寸/2.54
<img src="http://img.ui.cn/data/file/5/5/4/127455.png?imageView2/2/q/90"/>

####2.分辨率：屏幕上显示的像素个数，单位尺寸内像素点越多，显示的图像就越清楚。
分辨率720*1280表示手机水平方向的像素为720，垂直方向为1280.

####3.屏幕密度：表示屏幕每英寸有多少个像素。
240dpi（480*800） 、320dpi（720*1280）、480dpi（1080*1920）
<img src:"http://img.ui.cn/data/file/6/5/4/127456.png?imageView2/2/q/90"/>
（这里240dpi并不一定是480 * 800的分辨率，设计效果图时不用考虑这些，可以把480 * 800的分辨率“当成”是在240dpi下的设计，
因为实际240dpi下的分辨率可以和480 * 800的分辨率共用一套切图资源。）

####4.单位
dip:dot per inch，就是每英寸的像素数，也叫做屏幕密度。这个值越大，屏幕就越清晰。<br/>
ppi:#####对Android而言，DPI等价于PPI(Pixels-Per-Inch)<br/>
px：pixels(像素)，屏幕上的点，不同设备不同的显示屏显示效果相同，这是绝对像素，是多少就永远是多少不会改变。<br/>
dp：（andriod开发中用于描述尺寸和间距）与密度无关的像素。<br/>
sp：scaled pixels — best for text size (放大像素)（与刻度无关的像素）和dp一样，只是用于描述字号和行距。

####TODO
记录遇到过的机型信息<br/>
进一步创建相应机型的layout与values资源文件夹(用做测试)<br/>
