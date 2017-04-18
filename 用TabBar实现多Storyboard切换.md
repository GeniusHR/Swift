用TabBar实现多Storyboard切换
=====

01.新建一个名为 Study-MultiStoryboardWithTabBar 的 Single View Application 项目<br/>
![](http://ww1.sinaimg.cn/large/462fccedly1feql047mslj20d307v3zb.jpg)<br/>
02.在 Study-MultiStoryboardWithTabBar 项目下新建一个名为 First Group 的文件夹<br/>
03.在 First Group 文件夹中新建一个 Source 里 Cocoa Touch Class 的名为 FirstAViewController 的类，其中 Subclass of 选择 UIViewController 子类<br/>
![](http://ww1.sinaimg.cn/large/462fccedly1feql83f43cj208s03uwes.jpg)<br/>
![](http://ww1.sinaimg.cn/large/462fccedly1feql8r7yl6j20cn04smxh.jpg)<br/>
04.在 First Group 文件夹中新建一个 User Interface 的名为 First 的故事板<br/>
![](http://ww1.sinaimg.cn/large/462fccedly1feqlgjmy2zj208n03kglv.jpg)<br/>
![](http://ww1.sinaimg.cn/large/462fccedly1feqlaf5hwyj20af052aal.jpg)<br/>
05.在 First.storyboard 中拖入一个 View Controller 的视图<br/>
06.选中刚拖入的 View Controller 视图，选择右侧的 Identity inspector 选项卡，在 Custom Class 的 Class 中制定 FirstAViewController 类的绑定<br/>
![](http://ww1.sinaimg.cn/large/462fccedly1feqlhkhrbej206s02474e.jpg)<br/>
07.然后，在 Identity 的 Storyboard ID 中输入 JustFirstA 用于设定该故事板的第一个视图的名字<br/>
![](http://ww1.sinaimg.cn/large/462fccedly1feql6ab8evj206s02ndfx.jpg)<br/>
08.在 View Controller 中拖入一个 Label 控件，用于标示是第哪个故事板<br/>
09.重复2～8步，新建 Second Group 文件夹、SecondAViewController类、Second故事板和输入 JustSecondA 的视图名字<br/>
10.修改 ViewController 类里的继承类名为 UITabBarController 父累，用于 Main.storyboard 故事板底部实现切换标签<br/>
11.在 ViewController 类里的 viewDidLoad 方法中输入以下代码，用于实例化故事板<br/>
```Swift
   let FirstSB = UIStoryboard(name: "First", bundle: nil)
   let SecondSB = UIStoryboard(name: "Second", bundle: nil)
```
12.接下来输入以下代码，用于实例化各故事板中首先要显示的视图<br/>
```Swift
   let FirstVC = FirstSB.instantiateViewControllerWithIdentifier("JustFirstA")
   let SecondVC = SecondSB.instantiateViewControllerWithIdentifier("JustSecondA")
```
13.接下来输入以下代码，用于设定每个故事板首要视图标签的外观<br/>
```Swift
   FirstVC.tabBarItem = UITabBarItem(title: "FirstA", image: nil, tag: 0)
   SecondVC.tabBarItem = UITabBarItem(title: "SecondA", image: nil, tag: 0)
```
14.接下来输入以下代码，用于绑定 Main.storyboard 面板切换标签<br/>
```Swift
   self.viewControllers = [FirstVC, SecondVC]
```
15.运行
