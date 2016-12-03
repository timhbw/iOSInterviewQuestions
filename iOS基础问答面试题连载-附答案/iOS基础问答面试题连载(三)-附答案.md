>该文章属于**Timhbw**原创，转载请注明： <Timhbw>[https://github.com/Timhbw/iOSInterviewQuestions)


![iOSinterview.jpg](http://upload-images.jianshu.io/upload_images/3352035-35c38cf697870034.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


 <简书社区 — Timhbw>[iOS基础问答面试题连载(一)-附答案](http://www.jianshu.com/p/1ebf7333808d)
 <简书社区 — Timhbw>[iOS基础问答面试题连载(二)-附答案](http://www.jianshu.com/p/ce50261f8907)
 <简书社区 — Timhbw>[iOS基础问答面试题连载(三)-附答案](http://www.jianshu.com/p/5fd65c20912e)

####这次的问题是网络多线程相关的哟，面试的时候也是必问的，大家多看看

>11月24日修正一处错误:18、19题目一样,答案不一样(其实是两种理解，修改为最优的一种放上来.多谢读者提醒)


- 以下是一些自己收集的网络多线程方面比较基础的问题（大神可以忽略），附上答案，方便大家阅读。俗话说得好，基础不牢，地动山摇。文章末尾会提供PDF版的文档，方便大家木有网的时候也可以用移动设备观看。

##1.请简单说明多线程技术的优点和缺点？
- 优点：
    - 1.能够适当提高程序的执行效率；
    - 2.能够适当的提高资源的利用率，比如CPU、内存。
- 缺点：
    - 1.创建线程有额外开销
    - 2.程序的代码更加复杂
    - 3.线程越多，CPU在调度线程上的开销就越大
    - 4.如果开启大量线程，反而会降低程序的性能

##2.请简单说明线程和进程，以及他们之间的关系？
- 1.进程是CPU调度和分配资源的单位。
- 2.线程是CPU调用的最小单位
- 关系：
    - 1.进程包含线程；
    - 2.一个程序可以对应多个进程，一个进程中可以有多个线程，但至少要有一个线程；
    - 3.同一个进程内的线程共享进程的资源。

##3.请简单说明在iOS开发中有哪些多线程的实现方案？
- 1.PThread
- 2.NSThread
- 3.GCD
- 4.NSOperation

##4.请简单说明主线程的作用，以及使用注意点？
- 主线程:默认启动的线程
- 作用:(1)显示和刷新UI界面 (2)处理UI事件
- 注意点:
    - 1.不要将耗时操作放在主线程中执行
    - 2.UI操作必须在主线程中执行 !!!!

##5.请简单列出NSThread线程的几种状态，并说明状态转换的逻辑？
```
新建->就绪 CPU调度当前任务->运行->阻塞->死亡
                            CPU调度其他任务->就绪
```

##6.请简单说明如何简单的解决多线程访问同一块资源造成的线程安全的问题，以及注意点？
- 加同步(互斥)锁，
- @synchronized
- OC中的同步锁:(锁对象) + {要锁住的代码}
- 锁对象:要求是全局唯一的属性
  - 注意点:
    - 1.要注意加锁的位置
    - 2.加锁需要耗费性能,因此需要注意加锁的条件(多线程访问同一块资源)
    - 3.专业术语:线程同步

##7.请简单介绍下什么是原子和非原子属性？
- atomic：原子属性，会为setter方法加锁，默认为atomic。线程安全，会消耗大量资源
- nonatomic：非原子属性，不会为setter方法加锁。非线程安全，适合内存小的移动设备。

##8.请简单介绍下GCD这门技术？
- 全称 Grand Central Dispatch，牛逼的中枢调度器。
- GCD中有2个核心概念:任务和队列。
- GCD使用:封装任务，将封装好的任务添加到队列中，遵循FIFO。

##9.请简单介绍GCD中的几种队列？（4种）
- 并发队列：多个任务同时执行，会开启多个线程同时执行任务，只有在异步函数下才有效。
- 串行队列：任务只能一个接一个的去执行，不会开启多个线程，主队列属于串行队列，主队列所有的任务必须在主线程中执行。
- 全局队列
- 主队列

##10.如果当前有多个任务，这些任务都需要开子线程执行，而多个任务之间有一定的依赖关系，如果使用GCD来实现请试着给出一些解决方案。
- 使用异步函数（同步函数）+主队列

-----

##11.请简单说明单例模式的特点（作用）？
- 如果一个类实现了单例，那么可以保证在程序运行过程，一个类只有一个实例
- 单例对象易于供外界访问（通常会提供一个类方法）
- 实现了单例模式后，可以方便地控制了实例个数，并节约系统资源

##12.请简单介绍操作队列？
- 操作队列本身是OC语言的，在iOS开发中可以用来实现多线程编程
- 操作队列有两大核心的概念，一个是操作（NSOperation），一个是队列(NSOperationQueue),操作用来封装任务，队列用来存放操作
- 要使用操作队列进行多线程编程，只需要把封装好的操作提交到相应的队列中即可，系统内部会视情况自动开启相应的线程来执行任务
- 在操作队列这门技术中，系统提供了两个子类可以来封装任务，一个是NSInvocationOperation，一个是NSBlockOperation,除此之外也可以直接自定义操作
- 操作队列中有两种队列，一种是通过[NSOperationQueue mainQueue]获得的主队列，一种是通过[[NSOperationQueue alloc]init]方法获得的非主队列
- 主队列是和主线程相关的串行队列，提交到主队列中的操作将被安排在主线程中执行（可以利用该特性来处理线程间通信的相关逻辑）
- 操作+队列:
    - NSInvocationOperation
    - NSBlockOperatio
- NSOperationQueue
    - 自己创建 [[NSOperationQueue alloc]init];
    - 主队列   [NSOperationQueue main];

##13.如果有多个操作如何来设置依赖关系，如何监听到某个操作执行完毕事件？
- 1.设置依赖关系：假设有有两个操作分别是op1和op2，op1需要依赖于op2,那么只需要使用[op1 addDependency:op2]方法设置即可。
- 2.操作依赖补充：使用操作队列可以方便的指定多个操作间的依赖关系，甚至可以实现跨队列的操作依赖，但是在使用的时候需要注意操作之间不能有循环依赖关系
- 3.操作监听：可以使用^completionBlock来实现操作监听

##14.请简单比较GCD中的全局并发队列和使用dispatch_queue_create函数创建的并发队列异同？
- 1.全局并发队列在整个应用程序中本身是默认存在的并且对应有高优先级、默认优先级、低优先级和后台优先级一共四个并发队列，我们只是选择其中的一个直接拿来用。而Create函数是实打实的从头开始去创建一个队列。
- 2.在iOS6.0之前，在GCD中凡是使用了带Create和retain的函数在最后都需要做一次release操作。而主队列和全局并发队列不需要我们手动release。当然了，在iOS6.0之后GCD已经被纳入到了ARC的内存管理范畴中，即便是使用retain或者create函数创建的对象也不再需要开发人员手动释放，我们像对待普通OC对象一样对待GCD就OK。
- 3.在使用栅栏函数的时候，栅栏函数只有在和使用create函数自己的创建的并发队列一起使用的时候才有效
- 4.其它区别涉及到XNU内核的系统级线程编程，不一一列举。

##15.请简单说明对图片进行二级缓存的实现思路？
- 在显示图片的时候
    - 1.先检查该图片对应的内存缓存
        - 1.如果存在内存缓存，则
            - a.直接使用设置并显示图片；
        - 2.如果内存缓存中没有,则
            - a.继续检查该图片对应的磁盘缓存是否存在，跳转到第2步。
    - 2.检查该图片对应的磁盘缓存
        - 1.如果存在磁盘缓存，则
             - a.先保存一份到内存缓存中（方便下次使用）
             - b.然后设置并显示图片
        - 2.如果不存在磁盘缓存，则直接下载该图片，下载完成后
             - a.保存一份到内存缓存中
             - b.保存一份到磁盘缓存中
             - c.设置并显示图片

##16.请简单对比下GCD和NSOperation两种多线程的实现方案？
- GCD是纯C语言的API,而操作队列则是Object-C的对象。
- 在GCD中，任务用块（block）来表示，而块是个轻量级的数据结构；相反操作队列中的『操作』NSOperation则是个更加重量级的Object-C对象。
- 具体该使用GCD还是使用NSOperation需要看具体的情况，如果只是想简单开一个子线程执行任务推荐使用GCD，如果有很多任务需要开多个子线程下载推荐使用操作队列

##17.请按照自己的理解，说一说在进行多线程编程的时候相对于GCD而言，操作队列有哪些优势？
- NSOperation和NSOperationQueue的好处有：
    - 1.NSOperationQueue可以方便的调用cancel方法来取消某个操作，而GCD中的任务是无法被取消的（安排好任务之后就不管了）。
    - 2.NSOperation可以方便的指定操作间的依赖关系。
    - 3.NSOperation可以通过KVO提供对NSOperation对象的精细控制（如监听当前操作是否被取消或是否已经完成等）
    - 4.NSOperation可以方便的指定操作优先级。操作优先级表示此操作与队列中其它操作之间的优先关系，优先级高的操作先执行，优先级低的后执行。
    - 5.通过自定义NSOperation的子类可以实现操作重用

##18.请谈一谈，自定义操作的好处？
- 自定义操作，对操作进行封装，那么以后在使用的时候只需要alloc init即可，创建该操作的人不需要关系内部的代码实现，信息隐蔽。
- 自定义操作有助于代码重用

##19.请简单介绍GCD中的一次性代码?
- 1.一次性代码：

```  
   static dispatch_once_t onceToken;
     dispatch_once(&onceToken, ^{
        NSLog(@"-------");
     });
```
- 2.特点：
        - 在整个程序运行过程中block中的代码只会被执行一次
        - 一次性代码本身是线程安全的
- 3.常用于单例模式的实现中

##20.GCD中的dispatch_after是延迟把任务提交到队列还是先提交到队列再延迟执行？
- 是延迟之后在把任务提交到队列执行，把任务提交到队列中在延迟执行难度较大，不容易实现.

-----

##21.请说明NSRunloop和线程的关系?
- 线程和runloop是一一对应的关系(字典)
- 主线程对应的runloop是默认创建并启动的
- 子线程对应的runloop需要手动的创建并启动
- 如何获得子线程对应的runloop?[NSRunloop currentRunloop]该方法是懒加载的,在第一次调用该方法的时候发现该子线程对应的runloop不存在则会直接创建一个runloop保存并且返回.
- 线程销毁后runloop也要销毁

##22.请简单说明NSCache的特点
- NSCache是苹果推出专门用来处理内存缓存的类
- NSCache默认是线程安全的,在使用的时候可以不用考虑线程安全的问题
- NSCache使用方法和可变字典类似,当缓存文件超过最大限度的时候会开启一个回收过程,把最老的缓存对象回收
- NSCache可以设置缓存的const(成本)和缓存的数量

##23.请简单说明runloop中几个类之间的相互关系（runloop & source & timer &observer &mode）
- runloop启动之后会选择一种运行模式，在执行执行会先检查运行模式内部是否有source和timers,如果一个sourc或者是一个timer都没有那么runlooop启动之后就立刻退出了。
- runlooop的source有两种分类方法，按照以前的分类方法可以分为
    - 基于端口的
    - 自定义的
    - performSelector事件
    - 按照函数调用栈来划分，可以分为source0和soucr1。
- observer，可以用来监听当前runloop运行状态的改变，注意（Core foundation框架）
- NSTimer必须添加到runloop中才会工作，且其工作收到runloop运行模式的影响。
 
##24.请简单介绍下SDWebImage框架？
- SDWebImage框架是一款非常流行的用来处理图片下载和缓存的第三方框架
- SDWebImage框架为我们提供了高性能异步下载图片的方案，内部使用GCD等多线程相关技术
- 使用SDWebImage框架来下载图片，它内部默认会对图片进行内存缓存和磁盘缓存的二级缓存结构
- 该框架为UIButton,UIImageView等UI控件提供了分类，能够方便的处理相关控件图片的远程下载和缓存设置
- 该框架内部还提供了GIF图片播放，判断图片类型等一般功能

##25.请问SDWebImage框架内部在清理磁盘缓存的时候clearDisk方法和cleanDisk方法有什么区别？
- clearDisk:直接把整个缓存文件删除，删除之后创建一个新的空文件;
- cleanDisk:先删除过期的缓存文件，然后计算当前剩余缓存文件的大小,如果该数值超过设定的最大缓存大小，那么久安全文件创建的时间从远到近依次删除，直到整个剩余缓存文件大小小于设定的最大缓存大小为止。

##26.请问SDWebImage框架的框架结构是怎么样的？
- SDWebImage框架有几个主要的组件：
    - 管理者（SDWebImageManager) 
    - 缓存处理组件（SDImageCache）主要对下载的图片进行内存缓存和磁盘缓存处理
    - 下载处理组件（SDWebImageDownloader|SDWebImageDownloadOperation）主要处理开子线程异步发送网络请求下载图片相关操作

##27.请问SDWebImage框架内部怎么处理内存缓存的？
- 内部使用NSCache来专门处理内存缓存

##28.请简单说明NSRunloop的基本作用?
- 保持程序的持续运行
- 处理App中的各种事件（比如触摸事件、定时器事件、Selector事件）
- 节省CPU资源，提高程序性能：该做事时做事，该休息时休息

##29.什么是runloop?
- 从字面意思看：运行循环、跑圈.其实它内部就是do-while循环，在这个循环内部不断地处理各种任务（比如Source、Timer、Observer）
- 一个线程对应一个RunLoop，主线程的RunLoop默认已经启动，子线程的RunLoop得手动启动（调用run方法）
- RunLoop只能选择一个Mode启动，如果当前Mode中没
何Source(Sources0、Sources1)、Timer，那么就直接退出RunLoop

##30.runloop的自动释放池什么时候创建释放？
- 当runloop进入的时候会创建一个自动释放池。
- 当runloop退出的时候会把之前的自动释放池销毁。
- 当runloop即将进入休眠的时候会把之前的自动释放池先销毁，然后创建一个新的自动释放池。

-----

##31.请简单说明使用NSURLConnection发送网络请求的几种方法？
- 使用NSURLConnection发送同步请求（[NSURLConnection sendSync....]）
- 使用NSURLConnection发送异步请求1（[NSURLConnection sendAsync...]）
- 使用NSURLConnection发送异步请求2（设置代理，再发送网络请求）
```
同步 NSData *data = [NSURLConnection sendSync....]
异步 [NSURLConnection sendAsync]
代理 delegate
```

##32.请简单说明GET请求和POST个请求有什么区别,如何选择？
- GET请求的参数直接用&拼接并以？为分隔拼接在请求URL的后面
- POST请求的参数是转换为二进制设置在请求体传递的
- 如果仅仅只是索取数据获得数据，那么建议使用GET请求，其他情况则建议使用POST请求，相对而言POST请求安全性更好一些。

##33.请简单列出使用NSURLConnection发送一个异步POST网络请求的步骤?
- 1.确定请求路径（URL）
- 2.创建可变的请求对象（NSMutableURLRequest）
- 3.修改请求方法为POST请求
- 4.把参数拼接起来转换为二进制数据，设置请求体
- 5.使用NSURLConnection发送异步请求`([NSURLConnection sendAsync....])`
- 6.解析服务器返回的数据，查看请求结果

##34.请简单说明HTTP通信的过程？
- 1.请求：如果客户端想要获得相应的数据，那么就对着服务器发送一个请求，请求是客户端向服务器索要数据的过程。
- 2.响应：服务器接收到客户端的请求之后，需要对该请求作出反应，响应是服务器端把数据返回给客户端的过程。
- 3.请求分为两部分，一个是请求头，一个是请求体（GET请求没有请求体）。其中请求头是对客户端信息和请求本身的描述，而请求体存放要发送给服务器端的具体数据
- 4.响应分为两部分，一个是响应头，一个是响应体。其中响应头是对服务器端信息和响应数据本身的描述，而响应体存放要发送给客户端的具体数据。

##35.请简单说明NSURLSession对比NSURLConnection的优势？
- session支持http2.0协议(iOS 9.0 +)
- 在处理下载任务的时候可以直接把数据下载到磁盘
- 支持后台下载|上传
- 同一个session发送多个请求，只需要建立一次连接（复用了TCP）
- 提供了全局的session并且可以统一配置，使用更加方便
- 下载的时候是多线程异步处理的效率更高

##36.请简单列出NSURLSession发送POST请求的步骤？
- 1.确定请求路径(NSURL)
- 2.创建可变的请求对象(NSMutableURLRequest)
- 3.修改请求方法为POST(HTTPMethod)
- 4.把要传递的参数拼接，转换为二进制数据，设置为请求体(HTTPBody)
- 5.创建会话对象（NSURLSession shareSession）
- 6.根据会话对象来创建一个NSURLSessionDataTask任务
- 7.执行请求Task (需要调用Resume方法)
- 8.拿到服务器返回的数据之后，解析数据

##37.在发送网络请求的时候，如果请求路径中的参数有中文导致发送的网络请求失败，应该如何处理？
- 如果URL字符串中有中文，那么在进行使用发送请求的时候应该先对URL进行中文转码
- 相关方法：

```
[urlStr stringByAddingPercentEscapesUsingEncoding:NSUTF8StringEncoding]

```
##38.观察下面的代码，请问completionHandler在主线程还是子线程执行？
```
[[session dataTaskWithRequest:request completionHandler:^(NSData * _Nullable data, NSURLResponse * _Nullable response, NSError * _Nullable error) {

    //....

}] resume];

```

- completionHandler在子线程中执行。

##39.请简单介绍下网络响应的状态码？
- 状态码的职责是当客户端向服务器端发送请求时,描述返回的请求结果。借助状态码,用户可以知道服务器端是正常处理了请求还是出现了错误。
- 如200 OK状态码以3位数字+原因短语组成。数字中的第一位指定了响应的类别, 后两位无分类。
- 状态码分为五种类别，分别是：
    - 以1开头的（如100），定义范围为100~101，表示接收的请求正在处理，原因短语为Informational(信息性状 态码)。
    - 以2开头的（如200），定义范围为200~206，表示请求正常处理完毕，原因短语为Success(成功状态码)。
    - 以3开头的（如300），定义范围为300~305，表示需要进行附加的操作以完成网络请求，原因短语为Redirection(重定向状态 码)。
    - 以4开头的（如404），定义范围为400~415，表示客户端有错误，服务器无法处理请求，原因短语为Client error(客户端错误)。
    - 以5开头的（如500），定义范围为500~505，表示服务器端处理请求出错，原因短语为Server error(服务器错误)。

##40.使用NSURLSession发送网络请求的时候，最多可以建立多少个TCP连接？
- 在iOS中最多可以建立4个连接，在OSX中默认最多可以建立6个连接。
- 在iOS中NSURLSessionConguration内部有`HTTPMaximumConnectionsPerHost`属性,可以设置连接的数 量:The default value is 6 in OS X, or 4 in iOS
- 说明：
    - 由于HTTP/1.1 不支持多路复用,因此如果要处理多个网络请求,在处理HTTP请求的时候 多数浏览器厂商都是不假思索的就在客户端排队所有的HTTP请求,然后通过一个持久连接,一个接着一个的发送这些请求。然而这种方式性能实在太差。实际上,浏览器开发商对于对于此性能问题,尚没有任何更好的办法,因此只能允许客户端并行打开多个TCP连接会话。但是具体最多可以打开多少个TCP连接是有数量限制的, 多数现代的浏览器,包括桌面和移动浏览器,都支持打开6个连接。即客户端可以并行分派最多6个请求,服务器可以并行处理最多6个请求。
    - 为什么是6个连接?有什么特殊的意义吗?其实，这个数字是多方平衡后的结果:这个数字越大,便能够带来更多的请求并行能力,但是同样的客户端和服务器端所占用的资源也会越多。因此,每个主机6个连接只不过是大家都觉得比较安全,能够接受的一个数字而已。

-----

##41.请简单介绍JSON和XML？
- JSON和XML都是一种用来表示数据的一种数据格式，JSON更加轻量级。
- 服务器返回的数据通常是JSON的或者是XML的两种，JSON数据格式和OC对象中字典和数组有些相似，XML又称为XML文档，XML的语法结构由三部分构成分别是文档声明，元素和属性。
- 如果服务器返回的数据是JSON，那么在开发中通常需要对JSON数据进行反序列化处理，把JSON数据转换为OC对象。
- 如果服务器返回的数据是XML格式的，那么需要对XML文档进行解析，解析XML的方式有两种，分别是SAX（从根元素开始解析）和DOM(先把整个XML文档加载进内存再解析)

##42.JSON格式中的true和false,对应OC中的什么数据类型，值为多少？
- true和false对应OC中的NSNumber数据类型
- true对应的值为1，false对应的值为0

##43.请简单说明什么是序列化和反序列处理，用到了什么方法？
- 反序列化处理，即把JSON数据--->OC对象，使用的方法为：`[NSJSONSerialization JSONObjectWithData:jsonData options:kNilOptions error:nil]`
- 序列化处理，即把OC对象--->JSON数据，使用的方法为：`[NSJSONSerialization dataWithJSONObject:jsonString options:0 error:nil]`,注意并不是所有的OC对象都能够序列化为JSON数据

##44.请简单说明输出流的使用步骤【应用于文件下载时】和注意点？
- 使用步骤：
    - 1.创建输出流（指定路径）
    - 2.打开输出流（open）
    - 3.使用输出流写数据 （write...）
    - 4.关闭输出流 （close）
- 注意点：数据写完之后一定要关闭输出流

##45.请简单说明文件句柄（NSFileHandle）的使用步骤【应用于文件下载时】和注意点？
- 使用步骤：
    - 1.创建空的文件（路径）
    - 2.创建文件句柄（指向文件） 默认指向开头
    - 3.使用文件句柄来写数据（内部边写数据边移动文件句柄指针）
    - 4.关闭文件句柄(closeFile)
    - 注意点：
      - 1.在写使用文件句柄指针写数据的时候，内部会自动移动文件句柄指针
      - 2.写数据的时候可以设置位置（偏移量），如设置从文件的末尾接着写数据
      - 3.使用完毕之后，应该把句柄关闭

##46.请简单介绍下NSURLSessionTask的几个子类？
- NSURLSessionTask是一个抽象类，如果要使用那么只能使用它的子类;
- NSURLSessionTask有两个子类，一个是NSURLSessionDataTask,该task可以用来处理一般的网络请求，如GET|POST请求等，一个是NSURLSessionDownloadTask,该downloadTask在处理下载请求的时候有很大的优势;
- NSURLSessionDataTask有一个子类为NSURLSessionUploadTask,该uploadTask在处理上传请求的时候有优势.

##47.请简单介绍在iOS开发中XML的几种解析方式？
- XML文档有两种解析模式，一种是SAX（从根元素开发一个接着一个的解析），一种是DOM(将整个XML文档加载进内存解析)
- 在iOS开发中常用的XML的解析方法有两种，一种是使用苹果原生的NSXMLParser来解析（该方法基于SAX）,一种是使用谷歌公司提供的第三方框架GDataXML来解析（该方法基于DOM）

```
DOM 一次性加载 GDataXML
SAX 一个元素一个元素的解析 NSXMLParser(创建解析器->设置代理->开始解析)
```

##48.如何解决session设置代理之后对代理对象的强引用问题？
- NSURLSession对象在使用的时候，如果设置了代理，那么session对代理对象会保持一个强引用，在合适的时候应该主动进行释放
- 可以在控制器调用viewDidDisappear方法的时候来进行处理，可以通过调用invalidateAndCancel方法或者是finishTasksAndInvalidate方法来释放对代理对象的强引用
- invalidateAndCancel方法直接取消请求然后释放代理对象，finishTasksAndInvalidate方法等请求完成之后释放代理对象。

##49.在XCode中如何配置以MRC的方式来编译处理某个类？
- 点击项目的Targets，点击Build phases(编译阶段)，点击展开Compile Sources,找到要处理的类，配置为-fno-objc-arc即可。

##50.在使用NSURLSessionDataTask发送请求下载文件的时候，实现断点下载的技术要点是什么？
- 所谓断点下载，即只下载完整文件中的某一部分数据，如该文件有10M，那么需要做到只请求下载这个文件中5M~10M的这部分数据
- 可以通过设置请求头信息来实现，参考代码如下：

```
 NSString *header = [NSString stringWithFormat:@"bytes=%zd-",self.currentSize];
 [request setValue:header forHTTPHeaderField:@"Range"]
 ```

-----

##51.请简单比较使用NSURLSessionDownloadTask下载文件和使用NSURLSessionDataTask下载文件的优劣？
- NSURLSessionDataTask下载文件的优点：可以实现离线断点下载。缺点：代码复杂
- NSURLSessionDownloadTask下载文件的优点：
    - 内部已经完成了边接收数据边写入到沙盒中的操作（解决了下载大文件时候的内存飙升问题）
    - 可以方便的实现断点下载
- 缺点：无法实现离线断点下载

##52.请列出使用NSURLSession发送请求实现文件上传的主要步骤？
- 1.确定上传请求的路径 （NSURL）
- 2.创建可变的请求对象（NSMutableURLRequest）
- 3.修改请求方法为POST
- 4.设置请求头信息（告知服务器端这是一个文件上传请求）
- 5.按照固定的格式拼接要上传的文件等参数
- 6.根据请求对象创建会话对象（NSURLSession对象）
- 7.根据session对象来创建一个uploadTask上传请求任务
- 8.执行该上传请求任务（调用resume方法）
- 9.得到服务器返回的数据，解析数据（上传成功|上传失败）

##53.请列出你认为在进行文件上传时候需要注意的细节(注意点)？
- 1.创建可变的请求对象，因为需要修改请求方法为POST，设置请求头信息
- 2.设置请求头这个步骤可能会被遗漏
- 3.要处理上传参数的时候，一定要按照固定的格式来进行拼接
- 4.需要采用合适的方法来获得上传文件的二进制数据类型（MIMEType）

##54.请简单说明能够获得文件二进制数据类型（MIMEType）的几种方法？
- 直接百度 搜索
- 对着该文件发送一个网络请求，接受到该请求响应的时候，可以通过响应头信息中的MIMEType属性得到
- 使用通用的二进制数据类型表示任意的二进制数据 application/octet-stream
- 调用C语言的API来实现

##55.请简单介绍下AFN各个主要版本的情况？
```
 0.1--1.0            "2.0---2.6.3"                    3.0-->3.1.0
 NSURLConnection - (NSURLConnection + NSURLSession) - NSURLSessio

0.1-2.0  NSURLConnection
2.0 -3.0 NSURLSession + NSURLConnection
3.0 + NSURLSession

```

##56.如果服务器返回的数据不是JSON数据，那么在使用AFN发送网络请求的时候会请求失败请问是什么原因产生的？如何解决？
- AFN在接受到服务器返回数据的时候，内部默认采用以JSON的方式来对响应体信息进行反序列化处理，而如果服务器返回的数据不是JSON而是其他数据比如XML数据或者是图片数据的时候就会提示网络请求失败
- 如果服务器返回的数据不是JSON，那么应该修改AFN对响应的解析方式
    - 如果是XML数据，则:
```
manager.responseSerializer = [AFXMLParserResponseSerializer serializer]
```
    - 如果既不是JSON也不是XML，则manager.responseSerializer = [AFHTTPResponseSerializer serializer]

##57.在使用NSURLSession进行文件上传的时候，如何监听文件上传的进度，有哪些注意点？

- 创建会话对象的时候，需要设置代理，让控制器成为session的代理

- 遵守代理协议（NSURLSessionDataDelegate）

- 实现代理方法，在代理方法中计算文件的上传进度

```
         - (void)URLSession:(NSURLSession *)session task:(NSURLSessionTask *)task

         didSendBodyData:(int64_t)bytesSent

         totalBytesSent:(int64_t)totalBytesSent

         totalBytesExpectedToSend:(int64_t)totalBytesExpectedToSend
``` 
- 注意：当任务执行完毕的时候应该释放对代理对象的强引用

##58.请简单说明系统默认提供的NSURLSessionConfiguration三种配置信息？

- "defaultSessionConfiguration"返回标准配置，这实际上与NSURLConnection的网络协议栈是一样的，具有相同的共享NSHTTPCookieStorage，共享NSURLCache和共享NSURLCredentialStorage

- "ephemeralSessionConfiguration"返回一个预设配置，没有持久性存储的缓存，Cookie或证书。这对于实现像"秘密浏览"功能的功能来说，是很理想的

- "backgroundSessionConfiguration"：独特之处在于，它会创建一个后台会话。后台会话不同于常规的，普通的会话，它甚至可以在应用程序挂起，退出，崩溃的情况下运行上传和下载任务。初始化时指定的标识符，被用于向任何可能在进程外恢复后台传输的守护进程提供上下文

##59.在发送网络请求的时候，如果一个参数（place）需要对应着多个值，那么以下两种请求路径哪种是正确的？
```
①:[http://192.168.31.520:1314/loveyou?place=Beijing&Shanghai](http://120.25.226.186:32812/weather?place=Beijing&Shanghai)

②:[http://](http://120.25.226.186:32812/weather?place=Beijing&place=Shanghai)[192.168.31.520:1314](http://120.25.226.186:32812/weather?place=Beijing&Shanghai)/loveyou?place=Beijing&place=Shanghai

第二种请求路径是正确的，第一种是错误的，后面的shanghai将会被忽略
```

##60.使用AFN进行文件下载相对于NSURLSessionDownloadTask而言有何好处？

- 可以很方便的监听文件的下载进度

- NSURLSessionDownloadTask在实现文件下载的时候，内部默认把文件下载到了tmp临时路径，等下载完毕之后我们需要执行一个剪切操作

- AFN下载请求的实现内部基于NSURLSessionDownloadTask，在使用的时候只需要告知AFN应该把文件剪切到什么路径，那么AFN内部会自动的进行文件剪切处理

-----

##61.请简单回答网络安全的原则是什么？
- 在网络上"不允许"传输用户隐私数据的"明文"
- 在本地"不允许"保存用户隐私数据的"明文"

##62.请简单介绍下Base64编码？
- 特点：可以将任意的二进制数据进行Base64编码
- 结果：所有的数据都能被编码为并只用65个字符就能表示的文本文件。65字符：A~Z a~z 0~9 + / =
- 对文件进行base64编码后文件数据的变化：编码后的数据~=编码前数据的4/3，会大1/3左右。
- Base64编码原理:
    - 将所有字符转化为ASCII码；

    - 将ASCII码转化为8位二进制；

    - 将二进制3个归成一组(不足3个在后边补0)共24位，再拆分成4组，每组6位；

    - 统一在6位二进制前补两个0凑足8位；

    - 将补0后的二进制转为十进制；

    - 从Base64编码表获取十进制对应的Base64编码

##63.请简单说明单向散列函数的特点？
- 加密后密文的长度是定长的
- 如果明文不一样，那么散列后的结果一定不一样
- 如果明文一样，那么加密后的密文一定一样（对相同数据加密，加密后的密文一样）
- 所有的加密算法是公开的
- 不可以逆推反算
  - 总结：
    - 1 不可逆
    - 2 原文相同 散列值相同
    - 3 原文不同 散列值不同
    - 4 加密后密文的长度是定长的

##64.请简单介绍下散列函数的一些应用领域？
- 搜索 多个关键字，先对每个关键字进行散列，然后多个关键字进行或运算，如果值一致则搜索结果一致
- 版权 对文件进行散列判断该文件是否是正版或原版的
- 文件完整性验证 对整个文件进行散列，比较散列值判断文件是否完整或被篡改

##65.请简单介绍下对称加密的特点和经典算法？
- 特点:
    - 加密和解密使用相同的秘钥
    - 加密和解密的过程是可逆的
    - 性能好，效率高
- 经典算法
    - DES 数据加密标准
    - 3DES 使用3个密钥，对消息进行（密钥1·加密）+（密钥2·解密）+（密钥3·加密）
    - AES 高级加密标准

##66.请简单说明ECB和CBC两种分组加密模式？
- ECB模式的全称为Electronic CodeBook模式。又成为电子密码本模式。
    - 特点：
        - 使用ECB模式加密的时候，相同的明文分组会被转换为相同的密文分组。
        - 类似于一个巨大的明文分组——密文分组的对照表。
- CBC模式全称为Cipher Block Chainning模式（密文分组链接模式|电子密码链条）
    - 特点：
        - 在CBC模式中，首先将明文分组与前一个密文分组进行XOR运算，然后再进行加密。

##67.请简单介绍下非对称加密的特点和经典算法？
- 非对称加密的特点:
    - 使用一个密钥对进行加密和解密，公钥加密，私钥解密
    - 公钥是公开的，私钥是保密的
    - 使用非对称加密来处理加密和解密的过程高度安全，但是效率低下，性能很差
- 经典算法：RSA

##68.请简单介绍下数字签名这门技术？
- 应用场景：需要严格验证发送方身份信息情况
- 数字签名原理
  - 客户端处理
       - 对"消息"进行 HASH 得到 "消息摘要"
       - 发送方使用自己的私钥对"消息摘要" 加密(数字签名)
       - 把数字签名附着在"报文"的末尾一起发送给接收方
  - 服务端处理
       - 对"消息" HASH 得到 "报文摘要"
       - 使用公钥对"数字签名" 解密
       - 对结果进行匹配

##69.数字证书和公钥什么关系？
- 数字证书就是对公钥进行数字签名
- 证书和驾照很相似，里面记有姓名、组织、地址等个人信息，以及属于此人的公钥，并有认证机构施加数字签名,只要看到公钥证书，我们就可以知道认证机构认证该公钥的确属于此人
- 数字证书的主要内容：
    - 公钥
    - 认证机构的数字签名

##70.请简单说明在安装cocoapods时，使用pod install命令安装框架后的大致过程？
- 1.分析依赖:该步骤会分析Podfile,查看不同类库之间的依赖情况。如果有多个类库依赖于同一个类库，但是依赖于不同的版本，那么cocoaPods会自动设置一个兼容的版本。
- 2.下载依赖:根据分析依赖的结果，下载指定版本的类库到本地项目中。
- 3.生成Pods项目：创建一个Pods项目专门用来编译和管理第三方框架，CocoaPods会将所需的框架，库等内容添加到项目中，并且进行相应的配置。
- 4.整合Pods项目：将Pods和项目整合到一个工作空间中，并且设置文件链接。


 


