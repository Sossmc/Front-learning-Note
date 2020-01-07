`UIViewController`类（及其子类） 的对象带有一组管理其视图层次结构的方法。当视图控制器在状态之间转换时，iOS会在适当的时候自动调用这些方法。当您创建视图控制器[子类](https://developer.apple.com/library/archive/referencelibrary/GettingStarted/DevelopiOSAppsSwift/GlossaryDefinitions.html#//apple_ref/doc/uid/TP40015214-CH12-SW14)（就像`ViewController`您一直在使用的类）时，它[继承](https://developer.apple.com/library/archive/referencelibrary/GettingStarted/DevelopiOSAppsSwift/GlossaryDefinitions.html#//apple_ref/doc/uid/TP40015214-CH12-SW45)了在其中定义的方法，`UIViewController`并允许您为每个方法添加自己的自定义行为。了解系统何时调用这些方法非常重要，这样您就可以在过程中的相应步骤中设置或拆除您正在显示的视图 - 这些都是您在课程后面需要做的事情。

![WWVC_vclife_2x.png](assets/WWVC_vclife_2x.png)

iOS调用`UIViewController`方法如下：

- `viewDidLoad()` - 在从故事板创建和加载视图控制器的内容视图（其视图层次结构的顶部）时调用。在调用此方法时，视图控制器的出口保证具有有效值。使用此方法执行视图控制器所需的任何其他设置。

  通常，iOS `viewDidLoad()`首次创建内容视图时只调用一次; 但是，在首次实例化控制器时，不一定要创建内容视图。相反，它是在系统或任何代码第一次访问控制器的`view`属性时延迟创建的。

- `viewWillAppear()` - 在视图控制器的内容视图添加到应用程序的视图层次结构之前。使用此方法可以触发在屏幕上显示内容视图之前需要执行的任何操作。尽管名称，只是因为系统调用此方法，它不保证内容视图将变得可见。视图可能被其他视图遮挡或隐藏。此方法仅表示内容视图即将添加到应用程序的视图层次结构中。

- `viewDidAppear()` - 在视图控制器的内容视图添加到应用程序的视图层次结构后立即调用。使用此方法可以在屏幕上显示视图时立即触发任何需要执行的操作，例如获取数据或显示动画。尽管名称，只是因为系统调用此方法，它不保证内容视图是可见的。视图可能被其他视图遮挡或隐藏。此方法仅表示内容视图已添加到应用程序的视图层次结构中。

- `viewWillDisappear()` - 在视图控制器的内容视图从应用程序的视图层次结构中删除之前。使用此方法执行清除任务，例如提交更改或重新签署第一响应者状态。尽管名称如此，但系统不会仅仅因为内容视图被隐藏或隐藏而调用此方法。仅在将要从应用程序的视图层次结构中删除内容视图时调用此方法。

- `viewDidDisappear()` - 在视图控制器的内容视图已从应用程序的视图层次结构中删除之后。使用此方法执行其他拆卸活动。尽管名称如此，但系统不会仅仅因为内容视图已隐藏或隐藏而调用此方法。仅在从应用程序的视图层次结构中删除内容视图时才调用此方法。