# Lesson0 全新的开始

## 教程说明

欢迎来到 LearningWebGPU 教程，本教程改写自原本的 LearningWebGL.com 的 WebGL 入门教程，而后者则是改编于经典的 Nehe 的 OpenGL 教程。在开始教程前，有一些大家需要知道的事情：

1. 目前 WebGPU 仍然处于草稿阶段，所有的 API 接口可能会在未来发生变化。

2. 目前浏览器对于 WebGPU 的实现和支持仍处于实验阶段，可能会发生一些因为浏览器实现导致的 Bug 或错误；另外，开启浏览器的试验功能可能会降低浏览器的安全性，所以你不应该使用学习 WebGPU 开发的浏览器作为主力浏览器，例如请不要在这个浏览器中浏览、输入个人隐私信息、不要进行网页支付等。

3. 考虑到 WebGPU 正式投入生产环境应该是数年后的事情，所以本教程中将会使用大量新的 ECMA Script 的新特性，这些特性可能并不被当下的浏览器和 JavaScript 引擎所支持。

4. 本系列的教程是针对那些已经具备相应编程知识但没有实际 3D 图形经验的人的；目标是让学习者创建并运行代码，并且明白代码其中的含义，从而快速地创建自己的 3D Web 页面。

5. 我编写这套教程是因为我在独立学习 WebGPU，所以教程中可能（非常可能）会有错误，所以还请风险自担。尽管如此，我还是会不断的修正 Bug 和改正其中的错误的，所以如果你发现了教程中的错误或其他任何改进建议，请在本教程的 Github 仓库的 Issue 页面提交。

下面，让我们正式开始第 0 课的内容。

## WebGL 不好用了吗？

> 什么是 WebGPU？我们为什么要学习 WebGPU？WebGL 不好用了吗？

相信很多人会有这样的疑惑，为什么大佬们要不断造轮子，让我们这些已然学不动的前端程序员不断学习新的东西。

事实上，这真的要从 WebGL 说起。

时间回溯到 2006 年，一位名叫 Vladimir Vukićević 的美籍塞尔维亚裔软件工程师， 开始对即将到来的 HTML `<canvas>` 标签进行 OpenGL 原型的实现工作，他称之为“Canvas 3D”。

Vladimir 同时也是 Mozilla 的员工，他的工作启发了 Mozilla 和当时另外一个重要的浏览器开发商 Opera；在 2007 年底，Mozilla 和 Opera 同时开始各自独立的 OpenGL 实现工作。

在 2009 年初，非营利性组织 Khronos Group —— 它同时也是 OpenGL 和其他一系列重要图形标准（例如现在的 Vulkan）的拥有者 —— 创建了 WebGL 工作组，初始成员主要包括 Apple、Google、Mozilla 和 Opera。

WebGL 的主要目是在网页中实现使用 GPU 加速的图形绘制和物理计算。 Khronos Group 在 2011 年 3 月正式发布 WebGL 1.0 标准。WebGL 1.0 是基于 OpenGL ES 2.0 的，这是一个非常完备的、成熟的图形标准，但和顶尖的图形应用相比（例如 AAA 级游戏）它依然显得有些过于基础，单薄无力，甚至落后。

于是 WebGL 工作组开始在 2013 年着手制定 WebGL 2.0 标准，但事情并没有想象中的那么顺利，直到 2017 年 2 月 WebGL 2.0 标准才被正式发布。WebGL 2.0 标准基于 OpenGL ES 3.0，Firefox 51、Chrome 56 和 Opera 43 版本率先实现了对其的支持。但是，直到现在，也就是 2019 年 12 月 29 日，在这个 Opera 早已作古的现代，Webkit（Apple Safari iOS/MacOS）依然没有正式支持 WebGL 2.0。

WebGL 的诞生和发展见证了现代化网络技术的迅猛发展和其中的利益纠葛。

- 在当年 IE 仍然处于垄断地位的时代，曾经毫无理由指责 WebGL 安全性并且打死也不会支持 WebGL 的微软，现在已经彻底抛弃了 IE 浏览器，全面拥抱了 Chromium，甚至还建议 Mozilla 也使用 Chromium；而微软旗下的 Babylon.js 现在已经成为了和 Three.js 并肩而立的 WebGL 两大主要引擎框架。

- 当年力挺 HTML5 并唾弃 Flash 的 Apple，在 Jobs 故去后，也抛弃了 OpenGL 这一开放标准，自立门户研发推出了全新的 Metal 图形框架。

- 而 WebGL 的拥有者，Khronos Group 也逐渐放弃了 OpenGL 这一 WebGL 标准的基础，全力打造现在的明星产品 Vulkan 标准。

- 同时 WebGL 也经历了 W3C 和 WHATWG 对于 HTML 标准从势不两立到携手归一的过程，也经历了 TC39 和 Node.js 对于 ECMA Script / JavaScript 标准的爱恨情仇。

- WebGL 的发展过程中也见证了如 TypeScript、CoffeeScript、Dart 这些 JavaScript “替代者”的诞生。

- WebGL 还迎来了如 WebAssembly 等新技术的问世，它们对于 WebGL 和网页图形能力提供了更强的辅助。

尽管如此，我依然认为 WebGL 或者说 OpenGL ES 其实是一个非常完备的图形标准，WebGL 之所以没有成为前端开发的主流技术之一，主要是因为 JavaScript 本身的孱弱。在 JavaScript 和 V8 引擎飞速发展的今天，WebGL 已经足够满足大部分网页设计师的创意需求。

另外，WebGL 的最主要贡献其实在于将例如 TypedArray 等技术带入到了网页端，让 JavaScript 可以进行二进制操作，并且历史上第一次允许开发者精确控制网页中的每一个像素，并启发了浏览器开发商如何更好的使用 GPU 进行网页渲染的加速，WebGL 最终证明了在网页上进行图形开发是完全可行的。

同时，为了更好的实现 WebGL 标准，Google 开发了 ANGLE 这一伟大的图形标准转换引擎，Apple 正是使用了这一框架实现了在 Metal 上对 OpenGL 的兼容，同时微软也使用 ANGLE 在 IE 11 上实现了部分 WebGL 的功能。它也算是 WebGL 带来的意外收获之一。

另一方面，和网页开发完全无关的计算机图形学业界也在这些年来发生了剧烈的变化。在 WebGL 诞生当年，还是 OpenGL 和 Dirext 3D 两虎相争的局面，但是现在已然变成了 D3D12、Vulkan、Metal 的三国演义。

经典 OpenGL 是一个非常有学术范儿的技术，它认为 GPU 的作用就是进行 3D 图形绘制，所以提供了固定管线，但这在一定程度上禁锢了开发者的发挥；事实上，从 4.0 版本开始，OpenGL 也已经抛弃了固定渲染管线。但为时已晚，现在 OpenGL 已经成为明日黄花。

随着并行计算、人工智能、机器学习、计算机神经网络、自动驾驶等技术应用的发展和显卡厂商的商业模式的拓宽，不甘寂寞也不满足于被限制在图形绘制领域的 GPU 厂商（主要是 Nvidia），都在不断推进 GPU 在图形渲染之外的计算能力。

于是，现在 D3D12、Vulkan、Metal 成为并列的三大现代图形框架，他们全面释放了 GPU 的可编程能力，让开发者可以最大限度的自由操控 GPU。

所以，在当年 PBR 渲染还被视为次时代的高端技术，现在已经是遍地开花；在当年遥不可及的光线追踪技术，现在已经可以藉由 Nvidia RTX 显卡的专门的硬件处理单元实现实时光线追踪；当年只能作为产品草稿图和预览图的 GPU 实时渲染，随着基于深度学习的人工智能降噪技术的提出，直接迈步成为生产环境可用的可靠渲染方式之一。

这些都是 WebGL 标准制定者在当年没有预见到的。

所以，就有了 WebGPU。

## WebGPU，网页图形的未来

WebGPU 是由 W3C GPU for the Web 社区工作组开发的新标准，其中包括 Apple、Mozilla、Microsoft、Google 等主要成员。

WebGPU 的目的在于提供现代 3D 图形和计算能力。和 WebGL 不一样的地方在于，WebGPU 并不是基于某个已经实现的本地图形标准制定的，而是参考了 Vulkan、Metal 和 D3D12 的 API 的设计理念，旨在基于这些本地图形标准，提供跨平台的高性能图形接口。

在 2016 年 6 月 8 日的 WebGL 工作组双年会上，Google 展示了题为“精确网页图形接口”的幻灯片演示，其中探索了构建一个全新的 API 来代替 WebGL 的想法和原则，并称之为“WebGL Next”。

2017 年 1 月 24 日，Khornos Group 举办了讨论 WebGL Next 的研讨会，Google 团队展示了运行在 Chromium 上基于 OpenGL 的全新图形 API 的原型，同时还可以基于 OpenGL 和 Metal 独立运行。这个被叫做 NXT 的图形标准原型借鉴了 Vulkan、D3D12 和 Metal API 的概念。同时，Apple 和 Mozilla 也展示了基于 Safari 和 Servo 的原型，二者都非常接近于 Metal API。

2017 年 2 月 7 日，Apple WebKit 团队正式向 W3C 社区工作组提出设计全新 API 的提案。同时他们还提出了一个名为 WebGPU 的技术概念验证的提案，这是一个基于苹果 Metal API 概念的图形标准。随后，工作组采纳了 WebGPU 这个名字作为未来新标准的命名，并将 Apple 最初的那个提案的名字改名为 WebMetal，以避免重名造成的误解和冲突。

2017 年 2 月 16 日，W3C 的 “GPU for the Web” 社区工作组正式成立，尽管此前 Apple、Google、Mozilla 都曾提出实验性原型，但最终只有 Apple 的提案正式进入了 “gpuweb-proposals” 的代码仓库。不久后，在 2017 年 3 月 21 日，Mozilla 向 Khronos Group 的代码仓库提交了一个基于 Vulkan 名为 WebGL Next 的提案。

2018 年 6 月 1 日，Google Chrome 团队宣布将开始着手 WebGPU 标准的实现工作。

## 现时的 WebGPU

作为网页图形的未来，在现在就开始学习 WebGPU 是非常有必要的。但是必须指出的是，WebGPU 并没有最终发布，仍处于草稿阶段，所以 API 接口可能会在未来发生频繁改变；另外，目前 WebGPU 其实是处于事实上的分裂状态，主要的分歧在于着色器语言。

WebGL 使用 OpenGL ES Shading Language，也就是通常所说的 GLSL ES 2.0/3.0 作为着色器语言。这是一种和 C 很像的语言，WebGL 直接把用 GLSL 写成的着色器程序源代码，用文本的形式提交给浏览器，然后浏览器内部再提交到 GPU 使用显卡驱动中的 OpenGL 实现进行编译(事实上，在大部分 Windows 操作系统上，浏览器会前面提到过的使用 ANGLE 引擎将 GLSL 转换为 DirectX 3D 使用的 HLSL 语言和接口，最终使用 DirectX 实现 WebGL 的绘制)。

但是基于文本的着色器语言给 WebGL 实现，也就是浏览器厂商带来了非常多的困难和 Bug，这些问题与语言本身没有关系，而是完全由基于文本字符串这一特性带来的。所以在 WebGPU 标准创建伊始，就有人[提出](https://github.com/gpuweb/gpuweb/issues/44)不要使用基于文本字符串的着色器语言，避免重走 WebGL 的弯路。

为此，标准的设计者提出了两种方案。

- 以 Apple 为代表的厂商，建议结合其他着色器语言的优点，重新发明一种新的着色器语言，Apple 称之为 WHLSL - Web High Level Shading Language。WHLSL 是一个力图追求完美的着色器语言，但是它的实现过于复杂，所以并没有活到面世那天。Apple 在失败后，重新提出了另一个方案，即 WSL - Web Shading Language，并且 Apple 坚持认为基于文本字符串的着色器语言更加适合 WebGPU 的特质，尤其是在 Web 和 Node.js 上 JavaScript 本身已经非常成熟的字符串处理技术。目前 Safari 上的 WebGPU 实现正是使用了这一语言。

- 以 Google 为代表的厂商，因为吃过 WebGL 时代的亏，建议使用基于二进制的着色器语言，也就是说，着色器代码需要先被编译成二进制，再提交给浏览器使用。这一派的厂商提出可以继续使用 GLSL 的最新的 4.5 版本作为编程语言，然后使用 WebAssembly 技术将 GLSL 4.5 根据 Vulkan 标准的 SPIR-V 着色器标准，编译成二进制。Google 的理由也很充分，首先基于文本字符串的着色器会带来麻烦，这个 WebGL 已经验证过了；其次，WebAssembly 已经可以很好的处理二进制操作；最后，Vulkan 的 SPIR-V 着色器实现非常优秀，可以直接借鉴来用。

所以，在现在网络上屈指可数的 WebGPU 示例中，有的只能用 WebKit Safari 打开，有的只能用 Chromium Chrome / Edge 打开。

WebGPU 工作组的 Github 页面中，有一部分专门标明了各个浏览器的实现进度和使用的着色器语言：https://github.com/gpuweb/gpuweb/wiki/Implementation-Status

## 本课程的 WebGPU

- 本课程使用 [Chrome Canary](https://www.google.com/chrome/canary/) 作为推荐的调试开发浏览器。下载后，输入 `about:flags`，搜索 `webgpu`，找到 `Unsafe WebGPU`, 设置其为 `Enabled`；你也可以通过命令行的形式，在 Chrome Canary 的快捷方式中添加 `--enable-unsafe-webgpu` 来启用 WebGPU。

> 警告：目前 Chrome 浏览器尚未完成 GPU 沙盒模式的实现，因此所有在 WebGPU 中和显卡的交互数据都可以被其他程序进程获得。因此，在学习本课程的同时，请一定不要在 Chrome Canary 中浏览、输入个人隐私信息，一定不要进行网络支付等行为。

- 本课程使用 GLSL 4.5 作为着色器语言，使用 [@webgpu/glslang](https://www.npmjs.com/package/@webgpu/glslang) 把 GLSL 通过 WebAssembly 编译成 Vulkan 的 SPIR-V。也就是说，本课程目前不支持在 MacOS 上使用 Safari 开发调试。

- 本课程使用 TypeScript 编写，主要原因是 TypeScript 作为一个强类型语言和 JavaScript 的超集，配合诸如 VS Code 等 IDE 可以很好的给出语法提示和错误纠正，WebGPU 工作组给我们提供了一个 WebGPU 的类型定义文件 [@webgpu/types](https://www.npmjs.com/package/@webgpu/types)， 通过语法提示我们可以更好的学习 WebGPU 标准。
