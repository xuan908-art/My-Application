 一、实验目的
熟悉 Android Studio 开发环境与项目结构
掌握使用 Gradle(Kotlin DSL)构建 Android 工程的方法
理解 Activity 生命周期与界面布局的基本原理
学习 AndroidX 组件及 ConstraintLayout 布局的使用

二、实验内容 
1. 项目结构搭建
按照 Android 标准工程组织代码,主要目录包括:
 MainActivity.java — 应用入口 Activity
 activity_main.xml — 界面布局文件
 AndroidManifest.xml — 应用清单配置
 build.gradle.kts — 模块级构建脚本

2. 主 Activity 实现
MainActivity.java 继承自AppCompatActivity,在onCreate中完成:
 调用EdgeToEdge.enable(this)启用边缘到边缘(沉浸式)显示
 通过setContentView加载布局
 使用ViewCompat.setOnApplyWindowInsetsListener监听并应用系统栏(状态栏、导航栏)内边距,保证内容不被遮挡

3. 界面布局
activity_main.xml 采用ConstraintLayout作为根布局,在父容器中心位置放置一个TextView,文本内容为"Hello World!",通过四向约束(Top/Bottom/Start/End到 parent)实现居中。
 
 4. 清单配置
在 AndroidManifest.xml 中声明MainActivity,并配置<intent-filter>包含MAIN action 与LAUNCHER category,使其作为应用启动入口;同时配置了adjustResize软键盘模式与备份规则。
 
 5. 单元测试
ExampleUnitTest.java 编写了基础断言测试,验证2 + 2 == 4,验证本地单元测试框架可用。

三、实验结果
 应用成功编译并生成app-debug.apk ,可在 API 24 及以上设备运行
 启动应用后,屏幕中央显示 "Hello World!" 文本,内容自适应系统栏,无遮挡现象
 单元测试通过,构建流程无报错

四、实验心得
1. Gradle Kotlin DSL 相比 Groovy 具有更好的代码补全与类型检查
2. EdgeToEdge + WindowInsetsCompat 是处理沉浸式显示的现代方案,相比旧的fitsSystemWindows属性更灵活
3. ConstraintLayout 通过约束实现扁平化布局,减少嵌套层级,提升渲染性能
4. AndroidX 已成为现代 Android 开发的标准基础库,AppCompatActivity 提供了向后兼容的 Activity 行为
5. 项目生成的 APK 位于 app-debug.apk ,包含通过 dexBuilder 生成的 dex 文件,体现了 Android 的编译产物结构
