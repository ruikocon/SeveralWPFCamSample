# SeveralWPFCamSample
一些使用WPF，C#实现控制Webcam录像截图的示例代码



### SampleOpenCVSharp
使用OpenCVSharp库实现控制webcam，设置分辨率，录像截图的示例



##### 项目说明：

1. 开启摄像头之后在某些机器上可能会非常慢，要等一会，解决办法是new VideoCapture(0, VideoCaptureAPIs.DSHOW)加个DSHOW的参数，但这样又会造成录像失败，目前还没解决

2. 项目为.Net 6，代码理论上适用于.Net 和 .NetFramework，但实测发现，.Net Framework下无法录像

3. 通过nuget安装OpenCVSharp4.Windows和OpenCVSharp4.WpfExtensions，后者用于图像转换

4. 图片和视频输出到执行文件所在目录下的"_SampleOpenCVSharp"子目录之中



##### 参考文档：

> OpenCVSharp官网地址 https://github.com/shimat/opencvsharp   （Apache-2.0协议）
>
> OpenCVSharp官网wiki  https://github.com/shimat/opencvsharp/wiki
>
> opencv sharp 库使用手册    https://shimat.github.io/opencvsharp_docs/html/d69c29a1-7fb1-4f78-82e9-79be971c3d03.htm





### SampleMediaCapture

使用微软UWP的MediaCapture类实现控制webcam，选择分辨率，录像截图的示例，适用于.Net Framework



##### 项目说明：

1. 项目为.Net Framework，代码只适用于.Net Framework，因为.Net5之后放弃了对WinRT的支持，无法使用MediaCapture类

2. Visual Studio开发环境需安装"工作负荷-使用C++的桌面开发"，因为下面的MediaCaptureWPF.Native.dll使用了本地代码

3. 添加MediaCaptureWPF 和 MediaCaptureWPF.Native 引用，dll放在dll子目录，或者去https://github.com/mmaitre314/MediaCaptureWPF

4. 在 工具 -> Nuget包管理器 -> 程序包管理器设置 -> 常规 之中将默认包管理器模式改为 PackageReference

5. 在Nuget之中添加 Microsoft.Toolkit.Wpf.UI.Controls 

6. 项目属性之中 目标平台确保为x64

7. 图片和视频输出到"我的图片\\\_SampleMediaCapture"，因为MediaCapture类移植自UWP，故此只能对我的图片目录进行读写



##### 参考文档：

> 微软官方实例  https://github.com/microsoft/Windows-universal-samples/tree/main/Samples/CameraResolution
>
> MediaCaptureWPF  https://github.com/mmaitre314/MediaCaptureWPF   （Apache-2.0协议）





### SampleAForge

使用AForge库实现控制webcam，选择分辨率，录像截图的示例。



##### 项目说明：

1. 项目为.Net Framework，使用AForge库，适用于.Net Framework和.Net，但库比较老了，录像功能在.Net下无法使用,，而且存在一些问题，使用起来也比较麻烦

2. 首先在nuget下安装Aforge.controls,Aforge.video,Aforge.video.DirectShow

3. 通过nuget安装Accord.Video.FFMPEG  用于编码为视频文件，但因为使用了ffmpeg解码器，**所以Accord.Video.FFMPEG采用GPL协议，请注意协议的问题**

​	***注意不要去找AForge.video.ffmpeg，已经很老了，很多坑，再说也找不到***

4. 添加system.drawing的引用，如果是.Net6，需要在nuget之中安装 system.drawing.common 

5. 添加对C:\Windows\Microsoft.NET\Framework64\v4.0.30319\WPF\WindowsFormsIntegration.dll 的引用

6. 上面两个引用，是为了在XAML之中使用WindowsFormsHost

7. 输出文件保存在可执行文件所在目录的_SampleAforge目录下



##### 参考文档：

> AForge官网 https://github.com/andrewkirillov/AForge.NET  如今是Accord的一部分 使用ffmpeg的部分为GPL协议，其他代码为LGPL协议
>
> Accord官网 http://accord-framework.net/index.html  部分为GPL协议，其他代码为LGPL协议







### SampleCaptura

使用DirectShowLib库和FFmpeg实现控制webcam录像截图的示例。



##### 项目说明：

1. 适用于.Net Framework和.Net，可以获取从摄像录像截图，但不能选择分辨率，获取摄像头图像和录像截图代码都抄自Captura，获取摄像头部分使用DirectShowLib，编码输出视频部分使用ffmpeg
2. ffmpeg需从官网下载GPL版的，将可执行文件和dll解压到指定目录，比如D:\ffmpeg，然后将FFmpegService.cs中的两处folderPath改为该目录
3. 从nuget之中添加DirectShowLib，添加对程序集System.Drawing的引用
4. 输出文件保存在可执行文件所在目录的_SampleCaptura目录下



##### 参考文档：

> DirectShowLib官网： https://directshownet.sourceforge.net/   LGPL 2.1协议
>
> Captura官网   https://github.com/MathewSachin/Captura    MIT协议
>
> FFmpeg官网  https://ffmpeg.org/    GPL协议













