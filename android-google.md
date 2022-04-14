## 界面布局器

### 总结

1. 布局编辑器可帮助创建Android应用的界面。
2. 在应用屏幕上看到的所有的内容几乎均属于View。
3. TextView是在应用中显示文本的界面元素。
4. ConstraintLayout是存放其他界面元素的容器。
5. 在ConstraintLayout中，必须为Views设置水平和垂直方向的约束条件。
6. 放置View的一种方式是使用外边距。
7. 外边距表示View离它所处容器的边缘有多远。
8. 可以在TextView上设置字体、文本大小和颜色等属性。

## Kotlin中的集合

### 总结

1. 集合是一组相关项。
2. 集合可以是可变的，也可以是不可变的。
3. 集合可以有序，也可以无序。
4. 集合课要求项具有唯一性，也可允许重复。
5. Kotlin支持不同类型的集合，包括列表、集和映射。
6. Kotlin提供了许多用于处理和转换集合的函数，包括`forEach`、`map`、`filter`、`sorted`等。
7. Lambda是没有名称但可立即作为表达式传递的函数。例如，{ a: Int -> a * 3 }
8. 高阶函数是指一个函数传递给另一个函数，或从一个函数返回一个函数。

## activity和intent

#### 总结

1. 显示intent用于导航到应用中的特定activity。

2. 隐式intent对应于特定的操作（例如打开链接或共享图片），并让系统来确定执行相应intent的方式。

3. 借助菜单选项，您可以向应用栏添加按钮和菜单。

4. 半生对象提供了一种将可重复使用的常量与某种类型（而不是该类型的实例）相关联的方式。

   

   ### 执行intent的方法如下：

   1. 获取对intent的引用。
   2. 创建一个`Intent`对象，并提供activity或intent类型（具体取决于是显示还是隐式）。
   3. 通过调用`putExtra()`传递任何需要的数据。
   4. 调用`startActivity()`，同时传入`intent`对象。

## 活动生命周期的阶段

![c803811f4cb4034b.png](https://developer.android.google.cn/codelabs/basic-android-kotlin-training-activity-lifecycle/img/c803811f4cb4034b.png)





![f6b25a71cec4e401.png](https://developer.android.google.cn/codelabs/basic-android-kotlin-training-activity-lifecycle/img/f6b25a71cec4e401.png)





![9be2255ff49e0af8.png](https://developer.android.google.cn/codelabs/basic-android-kotlin-training-activity-lifecycle/img/9be2255ff49e0af8.png)

### 活动生命周期

1. 生命周期是活动会切换的一组状态。活动生命周期第一次开始，到活动时间当时结束。

2. 当用户在活动之间以及应用外部导航时，每个活动会在活动生命周期中的状态之间切换。

3. 活动周期中显示的情况有一个核心方法，可以在`Activity`类中替换此类方法。`onCreate()`	`	onStart()``onPause()``onRestart()``onResume()``onStop()``onDestroy()`。

4. 在活动转换为添加周期状态时发生的行为，请选择适当的状态的方式来选择。

5. 在Android Studio中添加类框架替换方法，请选择`代码>覆盖方法`，或按`Command+o`。

   

### 使用日志进行记录

1. 使用Android日志记录API（特别是`Log`类），可以写入要在Android studio内的Logcat中显示的简短消息。
2. 可`Log.d()`编写调试消息。这里采用两个参数：使用标签（通常是类）和消息（一个简短的日志的字符串方法）。
3. 使用Android studio 中的Logcat窗口可查看系统日志，包括自定义写入的消息。



### 保留活动状态

1. 当应用程序进入后台时（就在系统调用`onStop()`之后），应用程序数据可以保存到捆绑包中。系统会自动保存一些应用程序（例如`EditText	`的内容）。
2. bundle时`Bundle`的实例值的集合。键时持续的字符串。
3. 使用`onSaveInstanceState()`方法从bundle中重新获取数据，有更常用的方式是使用`onCreate()`。`onCreate()`方法是存储bundle的`saveInstanceState`参数。
4. 如果`saveInstanceState`变量为`null`，则表示活动启动时没有状态包，并且没有可以检索的状态数据。
5. 使用键从捆绑中搜索数据，请使用以`get`大意的`Bundle`方法，例如getInt()。



### 配置变更

1. 当设备的情况发生了改变时，系统解决的最简单的方式就是组织重组活动。
2. 最常见的配置变化示例哦时用户将设备从桌面旋转为横屏模式，或者从外观转为模式。当设备发生变化或插入硬件键盘时，也会发生配置变化。
3. 当发生配置会调用所有生命周期的关闭时，然后，Android开始启动相应的活动，同时会启动所有生命周期。
4. 与进程关闭一样，系统会通过`onSaveInstanceState()`将应用程序的状态保存到bundle中。



### Fragment 和 Navigation 组件

#### 总结

1. Fragment 是可以嵌入到activity 中且可重复使用的界面片段。
2. fragment 的生命周期与activity的生命周期不同，前者的视图在`onViewCreate()`（而非`onCreateView()`）中设置。
3. FragmentContainerView`用于在其他activity中嵌入fragment，并可以管理fragment之间的导航。

##### 使用Navigation组件

1. 通过设置`FragmentContainerView`的`navGraph`属性，可以在一个activity内的多个fragment之间导航。
2. 可以使用`NavGraph`编辑器添加导航操作，还可以指定不同目的地之间的参数。
3. 虽然使用intent进行导航需要传入extra，但Navigation组件使用SafeArgs为导航操作自动生成类和方法，从而确保参数实现类型安全。

#### fragment的用例

1. 借助Navigation组件，许多应用可在耽搁activity中管理其整个布局，且所有导航都在fragmeny之间完成。
2. fragment可实现常见的布局模式，如平板电脑上的主/从布局，或同一activity中的多个标签页。