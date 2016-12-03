>该文章属于**Timhbw**原创，转载请注明： <Timhbw>[https://github.com/Timhbw/iOSInterviewQuestions)


![iOSinterview.jpg](http://upload-images.jianshu.io/upload_images/3352035-35c38cf697870034.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<**Timhbw**>[iOS基础问答面试题连载(一)-附答案](https://github.com/Timhbw/iOSInterviewQuestions/blob/master/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD-%E9%99%84%E7%AD%94%E6%A1%88/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD(%E4%B8%80)-%E9%99%84%E7%AD%94%E6%A1%88.md)
 <**Timhbw**>[iOS基础问答面试题连载(二)-附答案](https://github.com/Timhbw/iOSInterviewQuestions/blob/master/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD-%E9%99%84%E7%AD%94%E6%A1%88/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD(%E4%BA%8C)-%E9%99%84%E7%AD%94%E6%A1%88.md)
  <**Timhbw**>[iOS基础问答面试题连载(三)-附答案](https://github.com/Timhbw/iOSInterviewQuestions/blob/master/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD-%E9%99%84%E7%AD%94%E6%A1%88/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD(%E4%B8%89)-%E9%99%84%E7%AD%94%E6%A1%88.md)

- 以下是一些自己收集的比较基础的问题（大神可以忽略），附上答案，方便大家阅读。俗话说得好，基础不牢，地动山摇。文章末尾会提供PDF版的文档，方便大家木有网的时候也可以用移动设备观看。

##1.xcode5和xcode7区别?
- xcode7没有Frameworks文件夹,xcode7内部会自动帮你导入一些常见的框架.
- xcode7多了LaunchScreen.xib,LaunchScreen.xib设置启动界面,而且可以确定模拟器或者真机的真实尺寸,如果没有设置,默认4s的尺寸(320,480)
- xcode7没有pch文件
- xcode5当中也有info.plist,只不过它的名字很长.是工程的名称.
 
##2.pch文件原理?
- 把pch里面的所有内容导入到每个文件中去
 
##3.UIApplication常见功能?
- 设置应用提醒数字
- 设置连网状态
- 设置状态栏
- 跳转网页
 
##4.程序完整启动流程?
- 1.执行Main
- 2.执行UIApplicationMain函数.
- 3.创建UIApplication对象,并设置UIApplicationMain对象的代理.UIApplication的第三个参数就是UIApplication的名称,如果指定为nil,它会默认为UIApplication.UIApplication的第四个参数为UIApplication的代理.
- 4.开启一个主运行循环.保证应用程序不退出.
- 5.加载info.plist.加载配置文件.判断一下info.plist文件当中有没有Main storyboard file base name,里面有没有指定storyboard文件,如果有就去加载info.plist文件,如果没有,那么应用程序加载完毕.
    
##5.UIWindow是什么?
- UIWindow是一种特殊的UIView，通常在一个app中至少有一个UIWindow
- iOS程序启动完毕后，创建的第一个视图控件就是UIWindow，接着创建控制器的view，
- 最后将控制器的view添加到UIWindow上，于是控制器的view就显示在屏幕上了
- 一个iOS程序之所以能显示到屏幕上，完全是因为它有UIWindow
 
##6.手动创建窗口的步骤?
- 1.创建窗口,要有窗口显示,必须要有强引用.窗口也是控件,要想展示出来.必须得要有尺寸.
- 2.创建控制器
- 3.设置控制器为窗口的根控制器
- 4.显示窗口

##7.makeKeyAndVisible做了哪些事情?
- 让窗口成为显示状态.
- 把根控制器的View添加到窗口上面.
- 把当前窗口设置成应用程序的主窗口
 
##8.如何从从StoryBoard加载控制器?
-  加载指定的storyBoard
- 加载箭头所指向的控制器.
- 加载指定标识的控制器.
 
## 9.initWithNibName的加载过程?
- 如果没有指定名称.指定为nil,那么它就会去先加载跟它相同名称的Xib.
- 如果没有跟它相同名称的Xib,那么它就会再去加载跟它相同名称去点Controller的名字的Xib.- - 控制器的init方法会调用initWithNibName:方法.
 
##10.LoadView 作用以及使用LoadView的注意点?
- 控制器调用loadView方法创建控制器的view.它的默认做法是:
- 先去判断当前控制器是不是从StoryBoard当中加载的,如果是,那么它就会从StoryBoard当中加载控制器的View.
- 如果不是从StoryBoard当中加载的, 那么它还会判断是不是从Xib当中创建的控制器.如果是,那么它就会从xib加载控制器的View.
- 如果也不是从Xib加载的控制器.那么它就会创建一个空的UIView.设为当前控制器的View.
    - 注意点:
        - 一旦重写了loadView,表示需要自己创建控制器的View.
        - 如果控制器的View还没有赋值,就不能调用控制器View的get方法.会造成死循环.
     因为控制器View的get方法底层会调用loadView方法.
 
 -----

##11.UIPickView是什么控件,基本用法怎样的?
- UIPickView选择控件,用来供用户选择一些城市等.它的基本用法与tableView基本相似,要设置数据源,代理, 让其展示数据

##12.KVC底层实现?
- 拿字符串与当前类的属性进行匹配.如果匹配到,就给该属性赋值.
```  
   [flagItem setValue:obj forKeyPath:key];
```
- 1.会找有没有跟key值相同名称的set方法,如果有，就会调用set方法,把obj传入
- 2.如果说没有set方法.那么它会去找没有相同名称,并且带有下划线的成员属性,如果有就会给该属性赋值.
- 3.如果也没有带有下划线的成员属性,就看有没有跟它相同名称的成员属性,如果有就会给该属性赋值.
- 4.如果还没有跟它相同名称的成员属性,就会调用`setValue:(id)value
 forUndefinedKey:`
- 5.如果没有实现setValue: forUndefinedKey: 就直接报错

##13.导航控制器View的结构是怎样的?
- 一个专门存放栈顶控制器View的View
- 一个导航条,导航条的高度为44,Y值为20

##14.导航push做了哪些事情?
- 当调用push方法时, 会把要push的控制器添加到导航控制器管理的栈中,把之前导航控制器中栈顶控制器View给移除,把当前栈顶控制器添加上去.

##15.导航pop做了哪些事情?
- 当调用pop方法时, 会把要pop的控制器从栈里移除,把之前导航控制器中栈顶控制器View给移除,把当前栈顶控制器添加上去.

##16.如何设置导航条的内容?
- 导航条的内容由导航控制器的栈顶控制器的NavigationItem决定.

##17.导航控制器pop操作有哪些?
- 返回上一级
- 返回到根控制器
- 返回到指定的控制器.

##18.文本框如何拦截用户输入?
- 给指定的文件框,设置代理 ,实现代理方法.里面包括是否允许开始编辑,是否允许结束编辑,是否允许改变字符等等.

##19.如何自定义键盘?
- 自定义键盘,要继承系统的UITextField,设置文本框的一个属性,该属性名称为inputView.这样就可以把键盘定义成自己要想的View.

##20.导航控制器的作用?
- 导航控制器可以轻松的完成控制器之间的切换.其操作有push,pop等.

-----

##21.自动跳转与手动型跳转区别?
- 自动跳转:通过控件直接拖线的方式进行跳转
- 手动跳转:在跳转之前要去做一些处理工作. 必须得要执行`performSegueWithIdentifier:`才能跳转.

##22.什么时候使用代理 ,代理的步骤?
- 当一个对象发生某一件事时,想要把自己的东西传给别人.或是通知别人做某事使用代理.
- 使用场景: 上下级之间,通常是它的上一级成为它的代理.
- 步骤：     
    - 1.定义协议
    - 2.定义代理属性
    - 3.在.m文件当中调用代理方法 
    - 4.设置代理
    - 5.遵守协议
    - 6.实现协议方法
 
-----

##23.ios当中存储方式有哪些?
- XML属性列表(plist)
- Preference(偏好设置)
- NSKeyedArchiver,只有遵守NSCoding协议的对象才可以使用这种方式。
- SQLite
- Core Data

-----

##24.tableView性能优化
- 1.tableView的缓存机制.
- 2.在不等高Cell当中,提前计算Cell的行高.提前估一个行高.200-250
- 3.如果说Cell当中有圆形图片,图片不要用ImageView加载layer.corneadius裁剪去做.会造成离屏渲染. 用绘图Qurarzds裁剪,生成一张圆形的图片.
- 4.如果说图片的宽高,指定为小数点.会造成锯齿,造成锯齿就会导致离屏渲染
- 5.cell当中的ImageView的大小最好是跟UIImage是一样大,如果不一样大 它会对UIImage做形变操作.cell当中展示都是小图.小图的大小跟ImageView  点击放大,是再去用大的ImageView加载大图.
- 6.做tableView的时候一定要用真机.
- 7.如果是从网络加载数据,一定要放到子线程(异步加载)当中做.
- 8.加载完毕的数据一定做本地缓存.
- 9.cell当中不要动态的添加子控件.一般都在创建时,就把要出现的Cell给添加进去,暂时不要显示的,可隐藏.
- 10.尽量减少Cell内部子控件的个数.
- 11.如果控件非常多,把不需要与用户进行交互的控件.能过异步绘制出来.生成一张图片.把图片添加到cell当中


 


