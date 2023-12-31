---
title: 学习HTML-标题和章节
date: 2023-10-13
layout: post
categories: ["Web Development","Programming"]
tags: ["html"]
draft: true
---

在上一节中，您了解了即使您不知道页面上的单词的含义，当语义元素为文档提供有意义的结构时，其他元素 - 搜索引擎、辅助技术、未来的维护人员、新的团队成员——会理解文档的大纲。

在本节中，您将发现文档结构;您将回顾上一节中的章节元素;并标记应用程序的大纲。

### 网站头

让我们构建一个网站标题。您将从非语义标记开始，逐步找到一个好的解决方案，以便您可以一路了解 HTML 章节和标题元素的好处。

如果您很少甚至没有考虑标头的语义，您可能会使用如下代码：

```
<!-- start header -->
<div id="pageHeader">
  <div id="title">Machine Learning Workshop</div>
  <!-- navigation -->
  <div id="navigation">
    <a href="#reg">Register</a>
    <a href="#about">About</a>
    <a href="#teachers">Instructors</a>
    <a href="#feedback">Testimonials</a>
  </div>
  <!-- end navigation bar -->
</div>
<!-- end of header -->
```
CSS 可以使（几乎）任何标记看起来都正确。但对所有内容使用非语义 `<div>` 实际上会产生额外的工作。要使用 CSS 定位多个 `<div>` ，您最终需要使用 id 或类来标识内容。该代码还包括每个结束 `</div>` 的注释，以指示每个 `</div>` 结束哪个开始标记。

虽然 id 和 class 属性为样式和 JavaScript 提供了挂钩，但它们没有为屏幕阅读器和（大多数情况下）搜索引擎添加任何语义值。

您可以包含 role 属性来提供语义，以便为屏幕阅读器创建良好的辅助功能对象模型 (AOM)：

```
<!-- start header -->
<div role="banner">
  <div role="heading" aria-level="1">Machine Learning Workshop</div>
  <div role="navigation">
    <a href="#reg">Register</a>
    <a href="#about">About</a>
    <a href="#teachers">Instructors</a>
    <a href="#feedback">Testimonials</a>
  </div>
  <!-- end navigation bar -->
<div>
<!-- end of header -->
```
这至少提供了语义并允许在 CSS 中使用属性选择器，但它仍然添加注释来标识每个 `</div>` 关闭的是哪个 `<div>` 。

如果您了解 HTML，您所要做的就是考虑内容的用途。然后，您可以在语义上编写此代码，而无需使用 role 并且无需注释结束标记：

```
<header>
  <h1>Machine Learning Workshop</h1>
  <nav>
    <a href="#reg">Register</a>
    <a href="#about">About</a>
    <a href="#teachers">Instructors</a>
    <a href="#feedback">Testimonials</a>
  </nav>
</header>
```
此代码使用两个语义标志： `<header>` 和 `<nav>`。

 这是一个在main中的头部，`<header>` 元素并不总是一个位置标记。根据嵌套位置的不同，它具有不同的语义。当 `<header>` 位于顶层时，它就是站点 banner ，一个地标角色，您可能已经在 role 代码块中注意到了。当 `<header>` 嵌套在 `<main>` 、 `<article>` 或 `<section>` 中时，它只是将其标识为该部分的标头，而不是一个地标。

> landmark主要作用是表示网页区域结构，比如你可以将页面划分为，导航，横幅标语，和内容，这些区域HTML中有对应的元素标签，landmark把他们叫做地标，方便开发者在应用中实现无障碍访问。

`<nav>` 元素将内容标识为导航。由于此 `<nav>` 嵌套在网站标题中，因此它是网站的主要导航。如果它嵌套在 `<article>` 或 `<section>` 中，则它只是该部分的内部导航。通过使用语义元素，您构建了一个有意义的可访问性对象模型（AOM）。 AOM 使屏幕阅读器能够通知用户此部分包含一个主要导航块，用户可以导航或跳过该导航块。

使用 `</nav>`和 `</header>` 结束标记无需注释即可识别每个结束标记结束的元素。此外，对不同的元素使用不同的标签就不再需要 id 和 class 钩子。 CSS 选择器的特异性可能较低；您可以使用 header nav a 定位链接，而不必担心冲突。

您编写的标头只包含很少的 HTML，并且没有类或 id。使用语义 HTML 时，您不需要这样做。

### 站点页脚

让我们对网站页脚进行编码。

```
<footer>
  <p>&copy;2022 Machine Learning Workshop, LLC. All rights reserved.</p>
</footer>
```

与 `<header>` 类似，页脚是否是地标(landmark)取决于页脚的嵌套位置。当它是网站页脚时，它是一个地标，并且应该在每个页面上包含您想要的网站页脚信息，例如版权声明、联系信息以及指向您的隐私和 cookie 政策的链接。网站页脚的隐式角色是 contentinfo 。否则，页脚没有隐式角色，也不是地标，如以下 Chrome 中 AOM 的屏幕截图所示（其中有 `<article>` 以及 `<header>` 和 `<footer>` 和 `<footer>` 之间）。

在此屏幕截图中，有两个页脚：一个位于 <article> 中，一个位于顶层。顶层页脚是一个具有 contentinfo 隐含角色的地标。另一个页脚不是地标。 Chrome 将其显示为 FooterAsNonLandmark ； Firefox 将其显示为 section 。

这并不意味着您不应该使用 `<footer>` 。假设您有一个博客。该博客有一个具有隐式 contentinfo 角色的网站页脚。每篇博客文章还可以有一个 `<footer>` 。在博客的主登陆页面上，浏览器、搜索引擎和屏幕阅读器都知道主页脚是顶级页脚，并且所有其他页脚都与它们嵌套的帖子相关。

当 `<footer>`是 `<article>` 、 `<aside>` 、 `<main>` 、 `<nav>` 或 `<section>`的子节点 ，那么它就不是一个地标。如果帖子单独出现，根据标记，该页脚可能会被提升。

页脚通常是您可以找到联系信息的地方，这些信息包含在 `<address>` （联系地址元素）中。这是一个不太好命名的元素；它用于包含个人或组织的联系信息，而不是实际邮寄地址。

该模块以 <header> 和 <footer> 开头，因为它们的独特之处在于有时是标志性元素或“分段”元素。让我们通过讨论最常见的页面布局来介绍“全职”分区元素：

![https://web.dev/learn/html/headings-and-sections?hl=en](https://web.dev/static/learn/html/headings-and-sections/image/a-layout-a-header-three-31026f6b6c4b4_856.png)

具有页眉、两个侧边栏和页脚的布局被称为圣杯布局。标记此内容的方法有很多，包括：

```
<body>
  <header>Header</header>
  <nav>Nav</nav>
  <main>Content</main>
  <aside>Aside</aside>
  <footer>Footer</footer>
</body>
```
如果您正在创建博客，您可能在 <main> 中有一系列文章:

```
<body>
  <header>Header</header>
  <nav>Nav</nav>
  <main>
    <article>First post</article>
    <article>Second post</article>
  </main>
  <aside>Aside</aside>
  <footer>Footer</footer>
</body>
```
当使用语义元素时，浏览器能够创建有意义的可访问性树，使屏幕阅读器用户能够更轻松地导航。这里，通过站点 `<header>` 和 `<footer>` 提供 banner 和 contentinfo 。这里添加的新元素包括 `<main>` 、 `<aside>` 和 `<article>` ；另外，您之前使用过的 `<h1>` 和 `<nav>` ，以及您尚未使用过的 `<section>` 。

### `<main>`

有一个 `<main>` 地标元素。 `<main>` 元素标识文档的主要内容，每页只能有一个 `<main>`。

### `<aside>`

`<aside>` 用于与文档主要内容间接或切线相关的内容。例如，本文是关于 HTML 的。对于有关三个站点标头示例（div、角色和语义）的 CSS 选择器特异性的部分，切线相关的旁白可以包含在 `<aside>` 中；并且，与大多数内容一样， `<aside>` 可能会显示在侧边栏或调出框中。 `<aside>` 也是一个地标，具有 complementary 的隐含角色。

### `<article>`

嵌套在 `<main>` 中，我们添加了两个 `<article>` 元素。在第一个示例中，当主要内容只是一个单词，或者在现实世界中，只有一个内容部分时，这是不必要的。但是，如果您正在编写博客，如我们的第二个示例中所示，则每个帖子都应位于嵌套在 `<main>` 的 `<article>` 中。

`<article>` 代表完整的或独立的内容部分，原则上可以独立重用。像报纸上的文章一样思考一篇文章。在印刷品中，一篇有关新西兰总理杰辛达·阿德恩的新闻文章可能只出现在一个版块中，也许是世界新闻。在报纸的网站上，同一篇新闻文章可能会出现在主页、政治版块、Oceana 或亚太新闻版块中，并且根据新闻主题、体育、生活方式或技术版块，也许。该文章还可能出现在其他网站上，例如 Pocket 或 Yahoo News!

### `<section>`

当没有更具体的语义元素可供使用时， `<section>` 元素用于包含文档的通用独立部分。除了极少数例外，各节都应该有一个标题。

回到 Jacinda Ardern 的例子，在报纸的主页上，横幅将包含报纸的名称，后跟一个 `<main>` ，分为几个    `<section>` ，每个都有一个标题，例如“世界新闻”和“政治”；在每个部分中，您都会找到一系列 `<article>` 。在每个 `<article>` 中，您还可能会找到一个或多个 `<section>` 元素。如果您查看此页面，整个“标题和部分”部分就是 `<article>` 。然后这个 `<article>` 被分成几个 `<section>` ，包括 site header 、 site footer 和文档结构。文章本身有一个标题，每个部分也有一个标题。

`<section>` 不是一个地标，除非它有一个易于理解的名称；如果它具有可访问的名称，则隐式角色是 region 。应谨慎使用地标角色，以识别文档的较大整体部分。如果您的 `<main>` 包含两个或三个重要的子部分（包括每个子部分的可访问名称），则使用过多的标志性角色可能会在屏幕阅读器中产生“噪音”，从而导致难以理解页面的整体布局 `<section>` 可能是有益的。

### 标题 `<h1>~<h6>`

有六个标题元素： `<h1>` 、 `<h2>` 、 `<h3>` 、 `<h4>` 、 `<h5>` 和 `<h6>` 。每个代表一个等级， `<h1>` 是最高或最重要的节级别， `<h6>` 是最低的。

当标题嵌套在文档横幅  `<header>` 中时，它是应用程序或站点的标题。当嵌套在 `<main>` 中时，无论它是否嵌套在 `<main>` 的 `<header>` 中，它都是该页面的标题，而不是整个网站的标题。当嵌套在 `<article>` 或 `<section>` 中时，它是页面该子部分的标题。



### 原文

- [Headings and sections](https://web.dev/learn/html/headings-and-sections?hl=en)
- [什么是landmark](https://w3c.github.io/aria/#landmark)
- [landmark解释](https://www.cnblogs.com/jrjrzivvv/p/13624576.html)

