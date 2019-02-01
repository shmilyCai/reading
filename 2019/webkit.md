# webkit技术内幕

## 1. 浏览器和浏览器内核

HTML5包含了一系列的标准，共包含10个大的类别：
1. 离线（offline）
2. 存储（storage）
3. 连接（connectivity）
4. 文件访问（file access）
5. 语义（semantics）
6. 音频和视频（audio/video）
7. 3D和图形（3D/graphics）
8. 展示（presentation）
9. 性能（performance）
10. 其他（Nuts and bolts）

HTTP是一种构建在TCP/IP之上的应用层协议，用于传输HTML文本和所涉及的各种资源，包括图片和多媒体等。

HTTPS是HTTP的安全版本，加入了SSL/TLS，用于安全地传输数据

渲染就是根据描述或者定义构建数学模型，通过模型生成图像的过程。

浏览器的渲染引擎就是能够将HTML/CSS/Javascript文本及其相应的资源文件转换成图像结果的模块。

渲染引擎主要包括：
1. HTML解释器，解释HTML文本的解释器，主要作用是将HTML文本解释成DOM（文档对象模型）树，DOM是一种文档的表示方法。
2. CSS解释器，级联样式表的解释器，作用是为DOM中的各个元素对象计算出样式信息，从而计算最后网页的布局提供基础设施。
3. 布局，在DOM创建之后，Webkit需要将其中的元素对象同样式信息结合起来，计算它们的大小位置等布局信息，形成一个能够表示这所有信息的内部表示模型，
4. Javascript引擎，使用Javascript代码可以修改网页的内容，也能修改css的信息，JavaScript引擎能够解释JavaScript代码并通过DOM接口和CSSOM接口来修改网页内容和样式信息，从而改变渲染的结果
5. 绘图，使用图形库将布局计算后的各个网页的节点绘制成图像结果。

## 2. HTML网页和结构

着重剖析HTML网页的构成和结构，通过对它们的解释来帮助理解webkit的渲染过程。

## 3. Webkit架构和模块

描述webkit为支持渲染而包含的基本模块和架构，同时结合chromium的架构和实现，来理解webkit的组成和浏览器的组成。

## 4. 资源加载和网络栈

介绍webkit的网络和资源加载机制，以及资源缓存策略。同时，在分析chromium多进程资源加载和全新网络栈和协议基础上，介绍一些HTML网页高效的资源使用方法。

## 5. HTML解释器和DOM模型

主要介绍DOM模型等方面的技术，并且描述Webkit中HTML解释器和DOM内部表示。

## 6. CSS解释器和样式布局

详解css解释器，并描述CSS3的新功能和webkit的支持情况。之后，分析webkit如何利用css来计算布局的过程。

## 7. 渲染基础

介绍目前的渲染方式以及根据网页结构来设计支持渲染的各种内部数据表示，包括RenderObject树和RenderLayer树，最后详细展现软件渲染网页的过程

## 8. 硬件加速机制

描述GPU硬件在目前渲染中所起的作用。现代浏览器越来越依赖GPU硬件加速渲染基础，特别是HTML5引入的众多标准。

## 9. Javascript引擎

专注于现代JavaScript引擎的介绍，包括JavaScript和V8引擎，描述它们在网页渲染中的作用

## 10. 插件和JavaScript扩展

介绍浏览器中的插件机制和扩展机制，包括webkit的NPAPI插件机制，chromium浏览器中的扩展机制，PPAPI机制和NativeClient技术，通过这些技术可以增加JavaScriptAPI在扩展JavaScript语言中的能力

## 11. 多媒体

专注于Webkit对多媒体方面的支持，包括音频和视频。
详解webkit的内部原理和对最新的html5视频及音频的支持。

## 12. 安全机制

描述HTML指定的网页安全规范并解释webkit和chromium浏览器的应对之策。

## 13. 移动WebKit

描述webkit支持移动领域特定的功能，同时也包括新的渲染机制。

## 14. 调试机制

详解webkit中的调试模块webInspector，包括结构和原理等。

## 15. Web前端的未来

谈对web未来发展的看法和目前一些明显的趋势。





