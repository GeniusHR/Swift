01.新建一个名为 Study-MultiStoryboardWithButton 的 Single View Application 项目<br/>
02.在 Study-MultiStoryboardWithButton 项目下新建一个名为 First Group 的文件夹<br/>
03.在 First Group 文件夹中新建一个 User Interface 的名为 First 的故事板<br/>
04.在 First.storyboard 中拖入一个 View Controller 的视图<br/>
05.选中刚拖入的 View Controller 视图，选择右侧的 Identity inspector 选项卡，在 Identity 的 Storyboard ID 中输入 JustFirstA 用于设定该故事板的第一个视图的名字<br/>
06.在 View Controller 中拖入一个 Label 控件，用于标示是第哪个故事板<br/>
07.重复2～6步，新建 Second Group 文件夹、Second故事板和输入 JustSecondA 的视图名字<br/>
08.在MainStoryboard中拖入两个Button，并右键拖建两个Touch Up Inside方法<br/>
09.分别在SwitchFirst和SwitchSecond的两个Touch Up Inside方法中实现调用弹出框的方法，其中UIAlertControllerStyle.Alert类型实现的是中间弹出提示框的效果，而UIAlertControllerStyle.ActionSheet类型实现的是从底部向上推出提示框的效果，在YesAction对象的handler属性中实现对确认操作的函数指向<br/>

```Swift
@IBAction func SwitchFirst() {
     let AlertMsg = UIAlertController(title: "iOS学习", message: "真的要切换到 First 故事板么？", preferredStyle: UIAlertControllerStyle.Alert)
     let NoAction = UIAlertAction(title: "不切换", style: UIAlertActionStyle.Cancel, handler: nil)
     let YesAction = UIAlertAction(title: "切换", style: UIAlertActionStyle.Default, handler:  {(alertAction: UIAlertAction) -> () in self.SwitchStoryboard("First")})
     AlertMsg.addAction(NoAction)
     AlertMsg.addAction(YesAction)
     self.presentViewController(AlertMsg, animated: true, completion: nil)
}
@IBAction func SwitchSecond() {
     let AlertMsg = UIAlertController(title: "iOS学习", message: "是否要切换到 Second 故事板？", preferredStyle: UIAlertControllerStyle.ActionSheet)
     let NoAction = UIAlertAction(title: "不要", style: UIAlertActionStyle.Cancel, handler: nil)
     let YesAction = UIAlertAction(title: "是的", style: UIAlertActionStyle.Default, handler: {(alertAction: UIAlertAction) -> () in self.SwitchStoryboard("Second")})
     AlertMsg.addAction(NoAction)
     AlertMsg.addAction(YesAction)
     self.presentViewController(AlertMsg, animated: true, completion: nil)
}
```
10.新建SwitchStoryboard方法以实现分别切换Storyboard
```Swift
func SwitchStoryboard(WhichStoryboard: String){
     switch WhichStoryboard{
          case "First":
               let FirstSB = UIStoryboard(name: "First", bundle: nil)
               let FirstVC = FirstSB.instantiateViewControllerWithIdentifier("JustFirstA")
               self.presentViewController(FirstVC, animated: true, completion: nil)
          break
          case "Second":
               let SecondSB = UIStoryboard(name: "Second", bundle: nil)
               let SecondVC = SecondSB.instantiateViewControllerWithIdentifier("JustSecondA")
               self.presentViewController(SecondVC, animated: true, completion: nil)
          break
          default :
          break
     }
}
```
