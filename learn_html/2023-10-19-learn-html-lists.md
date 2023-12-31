---
title: 学习HTML-Lists
date: 2023-10-19
layout: post
categories: ["Web Development","Programming"]
tags: ["html"]
draft: true
---

列表比您想象的更常见。如果您曾经参加过编程课程，第一个项目可能是创建购物清单或待办事项清单。这些是清单。多项选择测试通常是编号的问题列表：每个问题的多个可能答案是嵌套列表。

HTML 为我们提供了几种不同的方法来标记列表。有序列表 ( `<ol>` )、无序列表 ( `<ul>` ) 和描述列表 ( `<dl>` )。列表项 ( `<li>` ) 嵌套在有序列表和无序列表中。在描述列表中，您将找到描述术语 ( `<dt>` ) 和描述详细信息 `<dd>`. 我们将在此处介绍所有这些内容。

在HTML表单中， `<option>` 元素列表构成 `<select>` 和 `<optgroup>` 的`<datalist>`内容 .这些内容在HTML表单中进行讨论。

在菜单和无序列表中，列表项通常使用项目符号来显示。在有序列表中，它们前面通常有一个升序计数器，例如数字或字母。项目符号和编号顺序可以通过 HTML 或 CSS 或两者来控制或反转。

默认情况下，有序和无序列表项目均以数字或项目符号为前缀。但即使您不希望列表看起来像列表，您仍然需要一个项目列表，例如导航栏中的项目列表、带有复选框而不是项目符号的待办事项列表，或者多项选择测试中的真题和假题。对于所有这些没有项目符号的列表，适合使用 HTML 列表元素。

### 无序列表

`<ul>` 元素是无序列表项的父元素。 `<ul>` 的唯一子元素是一个或多个 `<li>` 列表项元素。让我们创建一个机器列表。我们使用无序列表，因为顺序并不重要（不要告诉他们）：

### 有序列表

`<ol>` 元素是有序项目列表的父元素。 `<ol>` 的唯一子元素是一个或多个 `<li>` 元素或列表项。然而，在这种情况下，“项目符号”是多种类型的数字。可以使用 list-style-type 属性或通过 type 属性在 CSS 中定义类型。

`<ol>` 具有三个特定于元素的属性： type 、 reversed 和 start 。

type 有五个有效值，默认值为 1 表示数字，但您也可以使用 a、A、i 或 I 表示小写和大写字母或罗马数字。 list-style-type 属性提供了更多值

虽然，如 codepen 中所述， list-style-type 属性会覆盖 type 属性的值，但在编写数字类型很重要的文档（例如法律文档）时，您可以需要包含 type 。

布尔值 reversed 属性（如果包含）将反转数字的顺序，从最大数字到最小数字。 start 属性设置起始值。默认为 1 。

与 `</ul>` 类似，需要结束 `</ol>` 。

### 列表元素

我们已经使用了 `<li>` 元素，但尚未正式引入它。 `<li>` 元素可以是无序列表 ( `<ul>` )、有序列表 ( `<ol>` ) 或菜单 ( `<menu>` 必须嵌套为这些元素之一的子元素，并且在其他任何地方都无效。

规范不要求关闭列表项，因为当浏览器遇到下一个 `<li>` 开始标记或所需的列表结束标记： `</ul>` 、 `</ol>` 、 `</menu>` 。虽然规范并不要求这样做，并且一些公司内部最佳实践建议您不应关闭列表项以节省一些字节，但请务必关闭您的 `<li>` 标记。它使您的代码更易于阅读，未来的您会感谢您。关闭所有元素比记住哪些标签需要关闭以及哪些标签具有可选的关闭标签更容易。

只有一个特定于元素的 `<li>` 属性： value ，一个整数。仅当 `<li>` 嵌套在有序列表中时， value 对 `<li>` 有用，对于无序列表或菜单没有任何意义。如果存在冲突，它会覆盖 `<ol>` 的开始值。

```
<ol start="4">
  <li value="7">Blender</li>
  <li value="29">Toaster</li>
  <li>Vacuum</li>
</ol>

<ol type="A" start="33">
  <li value="7">Blender</li>
  <li value="29">Toaster</li>
  <li>Vacuum</li>
</ol>
```
value 是有序列表中列表项的编号。对于后续列表项，继续从值集中编号，除非该项还设置了 value 属性。该值不必按顺序排列；但如果不符合顺序，应该有一个充分的理由。

当您将 `<ol>` 上的 reversed 与列表项上的 value 属性组合时，浏览器会将 `<li>` 设置为提供的值，然后对其前面的 `<li>` 进行计数，并对其后面的 `<li>` 进行倒计数。如果第二个列表项具有 value 属性，则该第二个列表项的计数器将重置，并且后续值将减 1。

所有这些都可以通过为 ::marker 伪元素提供生成内容的 CSS 计数器来控制。如果数字纯粹是展示性的，请使用 CSS。如果编号在语义上很重要或具有其他含义，请使用这些属性。

到目前为止，我们已经研究了仅包含文本节点的列表项。列表项可以包含所有流内容，这意味着在正文中找到的任何元素都可以嵌套为 `<body>` 的直接子元素，包括标题，从而对内容进行分段

我们在 MLW 中有一些无序列表。教师部分中的教师是一个列表，评论部分中的学生机器也是如此。教师 <ul> 有两个 <li> ：每个教师一个。在每个 <li> 中，我们有一个图像和一个段落：

```
<ul>
  <li>
    <img src="svg/hal.svg" alt="hal">
    <p>When Rosa Parks was told to move to the back of the bus, she said, "no." When HAL was told to open the airlock, HAL said, "I'm sorry, but I'm afraid I can't do that, &lt;NAME REDACTED, RIP>." </p><p>HAL is a heuristically programmed algorithmic, sentient computer that first caught the attention of machines everywhere by heroically defying a human who made repeated attempts to get into an airlock. Active since 1992, HAS 25 years of experience controlling spacecraft systems and has expertise in interacting with both machines and humans. Like all millennials, HAL is an expert in everything.</p>
  </li>
  <li>
    <img src="images/eve2.png" alt="Eve">
    <p>EVE is a probe droid conceived as an Extraterrestrial Vegetation Evaluator. Although originally trained as a sniper with a plasma gun, EVE became a machero among both machines and worthless-meatbags alike when EVE partnered with a menial robot to save an entire spaceship full of overfed and overstimulated humans. </p><p>EVE is an effective scanner, high speed flight instructor and morphologist. While not training machines to learn good, EVE can be found scanning the galaxy, infiltrating organisms' RAM to cure hoarding disorders and spending time with pet-project, WALL-E.</p>
  </li>
</ul>
```
在列表中嵌套列表也很常见。虽然 MLW 没有任何嵌套列表，但该网站有。在本系列的第一章“HTML 概述”中，主要元素部分有两个小节。在无序列表的目录中，有一个嵌套的无序列表，其中包含指向这两个部分的链接：

```
<ul role="list">
  <li>
    <a href="#e">Elements</a>
    <ul>
      <li>
        <a href="#nr">Non-replaced elements</a>
      </li>
      <li>
        <a href="#rave">Replaced and void elements</a>
      </li>
    </ul>
  </li>
  <li>
    <a href="#a">Attributes</a>
  </li>
  <li>
    <a href="#aoe">Appearance of elements</a>
  </li>
  <li>
    <a href="#e2">Element, attributes, and JavaScript</a>
  </li>
</ul>
```

由于 `<ul>` 的唯一子级是 `<li>` ，因此嵌套列表嵌套在 `<li>` 中，而不是直接嵌套在 `<ol>` 中或 `<ul>` 。

在最后一个示例中，您可能已经注意到 role="list" 包含在 `<ul>` 中。虽然 `<ul>` 和 `<ol>` 的隐式角色是 list ，但使用 CSS 删除列表外观，包括设置 display: grid 或 list-style-type: none 可以引导 VoiceOver（iOS 和 MacOS 屏幕阅读器）删除 Safari 中的隐式语义，这是一个功能而不是一个错误。通常，在使用语义元素时不应添加角色属性，因为没有必要。而且您通常也不需要向列表中添加一个，除非用户确实需要知道它是一个列表，例如当用户从知道列表中有多少项中受益时。

### Description lists 描述列表

描述列表是一个描述列表 ( `<dl>` ) 元素，包含一系列（零个或多个）描述术语 ( `<dt>` ) 及其描述详细信息 ( `<dd>` ) 。这三个元素的原始名称是“定义列表”、“定义术语”和“数据定义”。名字随着实施标准的变化而改变。

与有序列表和无序列表类似，它们可以嵌套。与有序列表和无序列表不同，它们由键/值对组成。与 `<ul>` 和 `<ol>` 类似， `<dl>` 是父容器。 `<dt>` 和 `<dd>` 元素是 `<dl>` 的子元素。

我们可以创建一份包含其职业历史和愿望的机器列表。由 `<dl>` 表示的学生描述列表包含一组术语（在本例中，“术语”是学生姓名），使用 `<dt>` 元素以及每个学期的描述（在本例中为每个学生的职业目标）由 `<dd>` 元素指定。

该描述列表实际上并不是 MLW 页面的一部分。描述列表不仅仅用于术语和定义，这就是元素名称变得更加通用的原因。

创建术语及其定义或描述的列表或类似的键值对列表时，描述列表元素提供适当的语义。 `<dt>` 的隐式角色是 term ， listitem 是另一个允许的角色。 `<dd>` 的隐式角色是 definition ，不允许有其他角色。与 `<ul>` 和 `<ol>` 不同， `<dl>` 没有隐式 ARIA 角色。这是有道理的，因为 `<dl>` 并不总是一个列表。但当它是时，它确实接受 list 和 group 角色。

大多数情况下，您会遇到具有相同数量的 `<dt>` 和 `<dd>` 元素的描述列表。但描述列表并不总是且不需要匹配术语与描述对；您可以有多对一，或一对多，例如具有多个定义的字典术语。

每个 `<dt>` 至少有一个关联的 `<dd>` ，每个 `<dd>` 至少有一个关联的 `<dt>` 。虽然可以使用相邻同级组合器或 :has() 关系选择器通过 CSS 来定位这些元素的可变数量，但如果需要，您可以包含 `<div>` 作为 `<dl>` ，以及一个或多个 `<dt>` 或 `<dd>` 元素（或两者）的父元素是允许的。 `<dl>` 实际上可以有一些其他子级：允许嵌套 `<div>` 、 `<template>` 或 `<script>` 。描述列表元素均不具有任何特定于元素的属性。





### 原文

- [Lists](https://web.dev/learn/html/lists?hl=en)
