>该文章属于**Timhbw**原创，转载请注明： <Timhbw>[https://github.com/Timhbw/iOSInterviewQuestions)


![iOSinterview.jpg](http://upload-images.jianshu.io/upload_images/3352035-ecfa8100bab890a1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



 <**Timhbw**>[iOS基础问答面试题连载(一)-附答案](https://github.com/Timhbw/iOSInterviewQuestions/blob/master/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD-%E9%99%84%E7%AD%94%E6%A1%88/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD(%E4%B8%80)-%E9%99%84%E7%AD%94%E6%A1%88.md)
 <**Timhbw**>[iOS基础问答面试题连载(二)-附答案](https://github.com/Timhbw/iOSInterviewQuestions/blob/master/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD-%E9%99%84%E7%AD%94%E6%A1%88/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD(%E4%BA%8C)-%E9%99%84%E7%AD%94%E6%A1%88.md)
  <**Timhbw**>[iOS基础问答面试题连载(三)-附答案](https://github.com/Timhbw/iOSInterviewQuestions/blob/master/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD-%E9%99%84%E7%AD%94%E6%A1%88/iOS%E5%9F%BA%E7%A1%80%E9%97%AE%E7%AD%94%E9%9D%A2%E8%AF%95%E9%A2%98%E8%BF%9E%E8%BD%BD(%E4%B8%89)-%E9%99%84%E7%AD%94%E6%A1%88.md)

- 以下是一些自己收集的比较基础的问题（大神可以忽略），附上答案，方便大家阅读。俗话说得好，基础不牢，地动山摇。文章末尾会提供PDF版的文档，方便大家木有网的时候也可以用移动设备观看。

##1.简单的描述下类扩展和分类的区别?(说2点)

- 类扩展没有名字,分类有名字

-  类扩展可以为某个类增加额外的属性、成员变量、方法声明;分类只能扩充方法,不能扩充成员变量,如果在分类中声明了一个属性,分类只会生成这个属性的get\set方法声明

##2.简要的说明UIView的frame和bounds的区别

- frame表示的是控件矩形框在父控件中的位置和尺寸,是以父控件的左上角为坐标原点.

- bounds表示的是控件矩形框的位置和尺寸,是以自己的左上角为坐标原点.

##3.什么是控制器

- 凡是继承自UIViewController的对象都是控制器.

##4.简单的描述控制器的作用

- 负责处理软件界面的各种事件,并负责软件界面的创建和销毁.

##5.简单的描述下storyboard的作用

- 用来描述描述软件界面的

##6.简述程序的启动原理

- 程序一启动，就会加载Main.storyboard文件;会创建箭头所指的控制器，并显示控制器所管理的软件界面

##7.IBOutLet有什么作用

- 被IBOutlet修饰的属性能拖线到storyboard中,而且只能修饰属性.

##8.IBAction有什么作用

- 被IBAction修饰的方法能拖线到storyboard中,只能修饰方法返回值类型

##9.IBAction和IBOutLet前缀IB是什么意思

- IB全称:Interface Builder,从Xcode4开始,Interface Builder已经整合到Xcode中

##10.简单描述父子控件

- 每个控件都是个容器，能容纳其他控件;内部小控件是大控件的子控件;大控件是内部小控件的父控件

-----

##11. 解释下引用资源的时候每个选项的含义
- copy:勾选copy,会把资源拷贝一份到项目的文件夹中(建议勾选,因为这样修改项目中的资源不会影响源资源)
- Added folder:如果勾选Create groups,只会会创建一个虚拟的文件夹,程序打包后,安装包中不存在这个文件夹;如果勾选Create folder references,真的创建一个文件夹,程序打包后,安装包中真的有这个文件夹.
- Add to targets:要不要把资源打包到软件安装包中去.一定要勾选,不勾选到时候程序打包后,安装包中没有这个资源.

##12.UILabel如何设置自动换行
- 设置numberOflines 为0.

##13.Character Wrap和Word Wrap的区别
- Character Wrap 字符包裹;
- Word Wrap 单词包裹<保证单词的完整性>

##14.contentMode的作用
- 内容模式: 一般用来控制图片如何显示

-----

##15.initWithImage:的作用?
- 根据传入的图片对象创建UIImageView对象;并且UIImageView的尺寸默认等于图片的尺寸

##16.如何修改一个控件的frame属性?
- 1.直接使用CGRectMake函数
- 2.利用临时结构体变量
- 3.直接运用结构体赋值

##17.如何抽方法?
- 先把相同的代码抽到方法中
- 把要变化的东西换成变量,然后编译,把报错的设置为方法的参数

##18.通过imageNamed:这个方法加载图片有什么特点?
- 有缓存
`UIImage *image =[UIImage imageNamed:@"图片名"]`
- 使用场合：图片比较小、使用频率比较高
- 建议：把需要缓存的图片放到Images.xcassets

##19.开发如何选择UILabel,UIImageView,UIButton
- 能用UILabel,UIImageView的尽量用UILabel,UIImageView;需要和用户交互用UIButton

-----

##20.什么是自定义控件
- 继承自系统的控件写一个自己的控件,目的是封装控件内部的细节

##21.通过代码如何自定义控件? 并且简单的描述下每一个步骤的理由?
- 新建一个继承UIView的类,(所谓自定义控件就是继承系统自带的控件写一个自己的控件)
- 在initWithFrame方法中添加子控件(保证别人在外面不管是通过init还是initWithFrame创建都能够添加子控件,因为init方法内部会调用initWithFrame                    
- 在layoutSubViews方法中设置子控件的frame(因为在InitWithFrame方法中当前控件尺寸可能没值,所以计算不了子控件的位置和尺寸,而在layoutSubViews方法,能够拿到当前控件的尺寸)
- 提供一个模型属性，重写模型属性的set方法(保证在别人在设置数据的那一刻就可以拿到数据设置到对应的子控件上)

##22.什么是模型
- 概念：专门用来存放数据的对象
- 特点：一般继承NSObject，在.h文件中声明一些用来存放数据的属性

##23.通过XIB如何自定义控件? 并且简单的描述下每一个步骤的理由?
- 1.新建一个继承UIView的类,(所谓自定义控件就是继承系统自带的控件写一个自己的控件)
- 2.新建一个xib文件（xib的文件名最好和类名一样）
- 3.修改最外面那个控件的class为控件类名(只有修改类名,当时候从xib中出来的才是我这种类型的控件)
- 4.提供一个模型属性，重写模型属性的set方法(保证在别人在设置数据的那一刻就可以拿到数据设置到对应的子控件上)

##24.instancetype和id的区别
- 都可以代表任意类型
- instancetype只能作为返回值
- id类型可以作为返回值,也可以作为参数,也可以定义变量
- instancetype会类型检测,id不会进行类型检测

##25. @property的使用策略
- assign:'基本数据类型'、’枚举‘、’结构体‘等非OC对象
- weak:OC对象类型（比如NSArray、NSDate、NSNumber、模型类）
- strong:OC对象类型（比如NSArray、NSDate、NSNumber、模型类）
- 一个对象只要有强指针引用，就不会被销毁

##26.懒加载的好处?
- 用到时再加载,只会加载一次

-----

##27.如果是通过xib或者storyboard创建控件，初始化的操作可以在initWithFrame:方法中做吗? 
- 如果是通过xib或者storyboard创建控件，初始化时是不会调用initWithFrame,会调用initWithCoder.初始化完毕会调用awakeFromNib方法,建议在awakeFromNib中做初始化

##28.通过alloc/init或者alloc/initWithFrame创建控件会不会主动加载xib?  
- 通过alloc/init或者alloc/initWithFrame创建控件不会主动加载xib,即使xib的名称和控件的类名一样

##29.用一个属性引用UI控件的时候为什么可以用weak?  
- 因为UI控件添加到父控件中以后,会有强指针指向这个对象,就应经可以保证这个对象不会被销毁.在搞一个属性引用这个对象,用弱引用就可以.

##30.如何隐藏一个控件?  
- 设置hidden为YES;
- 设置alpha为0.0.

##31.如何用按钮来实现图片上文字下的效果？
```
自定义按钮,实现
-（CGRect）titleRectForContentRect:(CGRect)contentRect
{
    // 返回文字的frame
}
-  (CGRect)imageRectForContentRect:(CGRect)contentRect
{
    // 返回图片的frame
}

- 自定义按钮,实现layoutSubViews方法调整按钮内部子控件的位置和尺寸
```

##32.通过代码如何设置的内边距?
```
self.btn.contentEdgeInsets = UIEdgeInsetsMake(30, 30, 0, 0);
self.btn.titleEdgeInsets = UIEdgeInsetsMake(0, -30, 0, 0);
self.btn.imageEdgeInsets = UIEdgeInsetsMake(0, -30, 0, 0);
```

#33.如何处理图片拉伸问题?
```
创建可拉伸的图片对象
bg = [bg resizableImageWithCapInsets:UIEdgeInsetsMake(10,10,10,10) resizingMode:..];//平铺和拉伸
UIImage *bg = ...
```

##34.在xcode中如何配置拉伸图片?  
- 选中图片--->右边(Slicing)-->Sices:Horizontal and Vertical -->上下左右设置

##35.KVC的作用?  
- Key Value Coding 键值编码,可以修改属性的值,并且可以修改私有的成员比变量;可以取值
-----

##36.如何监听scrollView停止滚动?
- 1.设置scrollView的代理
- 2.代理对象遵守<UIScrollViewDelegate>协议
- 3.实现协议里面

```
- (void)scrollViewDidEndDragging:(UIScrollView *)scrollView willDecelerate:(BOOL)decelerate
- (void)scrollViewDidEndDecelerating:(UIScrollView *)scrollView
```

##37.定时器一般有什么作用?以及如何使用定时器
- 可以办到每隔一定的时间做一件事件.
通过

```
+ (NSTimer *)scheduledTimerWithTimeInterval:(NSTimeInterval)ti target:(id)aTarget selector:(SEL)aSelector userInfo:(nullable id)userInfo repeats:(BOOL)yesOrNo; 
```
可以创建一个自定执行任务的定时器对象
- 通过 - (void)invalidate这个方法可以停止定时器

##38.scrollView的使用场景
- 当内容数据一多，在可视的View中就展示不完，这时候就需要用到UIScrollView控件.

##39.UIScrollView无法滚动的原因
- 1.没有设置contentSize,或者设置的contenSize小于等于scrollView的尺寸
- 2.scrollEnable = NO;
- 3.userInteractionEnable = NO; // 是否允许与用户交互

##40.scrollEnable和userInteractionEnable的区别
- 1.scrollEnable仅仅是不能滚动，其他事件依旧能够响应
- 2.userInteractionEnable禁止任何交互事件

##41.alwaysBounceVertical alwaysBounceHorizontal的作用
- 不管有没有contentSize，总是有弹簧效果;作用：用来做下拉刷新和上拉刷新的

##42.如何监听UIScrollView各种行为
- 1.设置scrollView的delegate（代理）为控制器对象
- 2.控制器要遵守协议UIScrollViewDelegate协议
- 3.控制器要实现UIScrollViewDelegate协议里面的方法

##43.代理的注意点
- 1.scrollView的代理可以是任何类型的OC 对象
- 2.代理一定是weak

##44.利用UIScrollView如何实现内容缩放
- 1.设置代理
- 2.实现代理方法
` -(UIView *)viewForZoomingInScrollview:(UIScrollView *)scrollView;`
- 3.设置缩放比例
```
self.scrollView.maximumZoomScale = 2.0;
self.scrollView.minimumZoomScale = 0.2;
```

##45.如何监听控件的行为？
- 1.通过addTarget:
只有继承来自UICotrol的对象，才有这个功能
- 2.通过delegate：
只有拥有delegate属性的控件，才有这个功能

-----

##46.通过autolayout如何实现UILabel包裹内容?

- 
1.设置位置约束

- 2.设置宽度约束<=固定值

- 3.不需要设置高度约束

##47.什么是适配?

- 适应、兼容各种不同的情况

- 系统适配:针对不同版本的操作系统进行适配

- 屏幕适配:针对不同大小的屏幕尺寸进行适配

##48.点和像素的区别

- 在用户眼中,屏幕是由无数个像素组成的,像素越多，屏幕越清晰

- 在开发者眼中,屏幕是由无数个点组成的，点又是由像素组成的,一个点钟包含的像素越多,屏幕越清晰.

##49.什么是Autolayout?

- Autolayout是一种“自动布局”技术，专门用来布局UI界面的

##50.简单描述下Autolayout的2个核心概念约束和参照

- 约束:通过给控件添加约束,来决定控件的位置和尺寸

- 参照:在添加约束时,是依照谁来添加(可以是父控件或者兄弟控件)

﻿

##51.Autolayout的警告和错误

- 警告:控件的frame不匹配所添加的约束

- 错误:1>缺乏必要的约束;2>两个约束冲突

##52.通过代码添加约束的原则

- 1.对于两个同层级view之间的约束关系，添加到它们的父view上

- 2.对于两个不同层级view之间的约束关系，添加到他们最近的共同父view上

- 3.对于有层次关系的两个view之间的约束关系，添加到层次较高的父view上

##53.什么是VFL

- 
VFL全称是Visual Format Language，翻译过来是“可视化格式语言”

- VFL是苹果公司为了简化Autolayout的编码而推出的抽象语言

##54.通过约束如何实现动画

- 在修改了约束之后，只要执行下面代码，就能做动画效果

```
[UIView animateWithDuration:1.0 animations:^{

    [添加了约束的view的父控件 layoutIfNeeded];

}];

```
-----

##55.性能优化的具体实现
- 当滚动列表时，部分UITableViewCell会移出窗口，UITableView会将窗口外的UITableViewCell放入一个对象池中，等待重用。
- 当UITableView要求dataSource返回UITableViewCell时，dataSource会先查看这个对象池，如果池中有未使用的UITableViewCell，dataSource会用新的数据配置这个UITableViewCell，然后返回给UITableView，重新显示到窗口中，从而避免创建新对象.

##56.UITableView如何展示数据?
- 1.设置数据源对象self.tableView.dataSource = self;
- 2.数据源对象要遵守协议
- 3.实现数据源方法

```
// 多少组数据
- (NSInteger)numberOfSectionsInTableView:(UITableView *)tableView;
// 每一组有多少行数据
- (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section;
// 每一行显示什么内容
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath;
```

##57.UITableView的有哪几种样式
- UITableViewStylePlain
- UITableViewStyleGrouped\

##58.UITableViewController的认识
- tableVieController有个tableView属性,指向一个tableView,而tableView的dataSource和delegate属性指向就是这个控制器.并且这个控制器已经遵守了UITableViewDataSource和UITableViewDelegate协议.而每个控制器的内部都有一个view属性,在tableVieController中,view和tableView属性指向的是同一个对象.

##59.性能优化的思路
- iOS设备的内存有限，如果用UITableView显示成千上万条数据，就需要成千上万个UITableViewCell对象的话，那将会耗尽iOS设备的内存。要解决该问题，需要重用UITableViewCell对象

##60.UITableView的性能优化的实现步骤
``` 
/**  每当一个cell要进入视野范围就会调用这个方法 */
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
{
    // 1.定义一个重用标识
    static NSString *ID = @"tim";
    // 2.去缓存池取可循环利用的cell
    UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:ID];
    
    // 3.缓存池如果没有可循环利用的cell,自己创建
    if (cell == nil) {
        cell = [[UITableViewCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:ID];
        // 建议:所有cell都一样的设置,写在这个大括号中;所有cell不都一样的设置写在外面
        cell.backgroundColor = [UIColor redColor];
        
    }
    // 4.设置数据
    cell.textLabel.text = [NSString stringWithFormat:@"第%zd行数据",indexPath.row];
    
    return cell;
}
```

##61.registerClass:的作用
- 根据一个ID注册这个ID标识对应的cell类型.

##62.通过注册的方法如何实现cell的重用
```
NSString *ID = @"wine";
- (void)viewDidLoad {
    [super viewDidLoad];
    // 注册ID 这个标识对应的cell类型为UITableViewCell
    [self.tableView registerClass:[UITableViewCell class] forCellReuseIdentifier:ID];
}
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
{
    // 1.先去缓存池中查找可循环利用的cell
    UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:ID];
    
    // 2.设置数据
    cell.textLabel.text = [NSString stringWithFormat:@"%zd行的数据", indexPath.row];
    
    return cell;
}
```

##63.如何监听tableView内部cell的点击事件
- 1.设置代理
- 2.代理对象遵守协议
- 3.实现协议里面的方法
-----

##64.简述`registerNib:(nullable UINib *)nib forCellReuseIdentifier:(NSString *)identifier`和`registerClass:(nullable Class)cellClass forCellReuseIdentifier:(NSString *)identifier`这2个方法的区别
- registerClass这个方法是根据ID 注册对应的cell类型,系统创建cell的方式是通过alloc/initWithStyle...
- registerNib 这个方法是根据ID 注册一个xib文件,系统创建cell的方式是通过加载xib文件.

##65.如何计算一段文字的宽度和高度?
- 第一种情况:如果label只有一行,通过sizeWithAttributes:这个方法,告知这段文字的字体和字体大小就可以计算这段文字的尺寸.
- 第二种情况:如果label需要换行计算高度,通过boundingRectWithSize: options: attributes:attributes context: 这个方法,告知这段文字的字体和字体大小,并且在一个限制的尺寸内计算这段文字的尺寸.

##66.什么是自定义cell?
- 继承自系统的UITableViewCell写一个自己的cell

##67.通过代码自定义cell能在ininWithFrame:方法中添加子控件吗?
- 不能,自定义cell 是在initWithStyle:reuseIdentifier:方法添加子控件

##68.通过代码自定义cell能在initWithStyle:reuseIdentifier:方法中计算子控件的位置和尺寸吗?
- 不行,因为在这个方法,cell的尺寸可能还没有,而计算子控件的位置和尺寸需要相对于cell来计算.通过代码自定义cell是在layoutSubviews中计算的

##69.通过代码自定义cell,frame和Autolayout2中的方式有什么区别?
- 这2种方法,只是子控件的位置和尺寸的确定方法不一样.frame是通过设置子控件的frame来确定;而Autolayout是通过添加约束的方式来确定

##70.通过storyboard的方式是如何加载cell
- 首先根据ID去缓存池中取,如果缓存中没有,也没有注册,会自动去storyboard中找有没有ID这种标识的Cell,如果有,会加载这个cell,并且绑定这个标识返回

##71.字典转模型第三方框架的了解
- Mantle:所有模型都必须继承自MTModel
- JSONModel:所有模型都必须继承自JSONModel
- MJExtension:不需要强制继承任何其他类

##72.设计框架需要考虑的问题
- 侵入性:侵入性大就意味着很难离开这个框架
- 易用性:比如少量代码实现N多功能
- 扩展性:很容易给这个框架增加新功能






