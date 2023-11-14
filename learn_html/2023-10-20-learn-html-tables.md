---
title: 学习HTML-Tables
date: 2023-10-20
layout: post
categories: ["Web Development","Programming"]
tags: ["html"]
draft: true
---

HTML 表格用于显示包含行和列的表格数据。使用 `<table>` 的决定应基于您所呈现的内容以及用户与该内容相关的需求。如果要呈现、比较、排序、计算或交叉引用数据，那么 `<table>` 可能是正确的选择。如果您只是想整齐地布置非表格内容（例如一大组缩略图），那么表格并不合适：相反，您可以创建一个图像列表并使用 CSS 设置网格样式。

在本节中，我们将讨论构成表格的所有元素，以及在呈现表格数据时应考虑的一些可访问性和可用性功能。虽然学习 HTML 本质上并不是关于 CSS，并且有一门完整的课程专门用于学习 CSS，但我们将介绍一些特定于表格的 CSS 属性。

### 表格元素

`<table>` 标签包裹表格内容，包括所有表格元素。 `<table>` 的隐式 ARIA 角色是 table ；辅助技术知道该元素是一个表结构，其中包含按行和列排列的数据。如果表格保持选择状态、具有二维导航或允许用户重新排列单元格顺序，请设置 role="grid" 。如果 grid 的行可以展开和折叠，请改用 role="treegrid" 。

在 `<table>` 内，您将找到表格标题 ( `<thead>` )、表格正文 ( `<tbody>` ) 以及可选的表格页脚 ( `<tfoot>` ) 组成。行包含表标题 ( `<th>` ) 和表数据 ( `<td>` ) 单元格，而这些单元格又包含所有数据。在 DOM 中，在此之前，您可能会发现两个附加功能：表格标题 ( `<caption>` ) 和列组 ( `<colgroup>` )。根据 `<colgroup>` 是否具有 span 属性，它可能包含嵌套表列 ( `<col>` ) 元素。

该表的子项按顺序为：

- `<caption>`
- `<colgroup>`
- `<thead>`
- `<tbody>`
- `<tfoot>`

我们将介绍 `<table>` 元素的子元素，它们都是可选的，但建议使用，然后查看行、表头单元格和表数据单元格。 `<colgroup>` 将在最后介绍。

### 表格标题

作为原生语义元素， `<caption>` 是为表命名的首选方法。 `<caption>` 提供了一个描述性的、以编程方式关联的表标题。默认情况下，它对所有用户可见且可用。

`<caption>`元素应该是嵌套在 `<table>` 元素中的第一个元素。包含它可以让所有用户立即了解表格的用途，而无需阅读周围的文本。或者，您可以在 `<table>` 上使用 aria-label 或 aria-labelledby 来提供可访问的名称作为标题。 `<caption>` 元素没有特定于元素的属性。



### 原文

- [Tables](https://web.dev/learn/html/tables?hl=en)
- [Table & CSS](https://estelle.github.io/CSS/tables/#slide1)


