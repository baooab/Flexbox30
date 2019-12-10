# Flexbox: 使用 Auto Margin 对齐

`align-self` 控制的是交叉轴上的 Flex 项目对齐。但问题来了，“在主轴上有没有类似的属性存在呢”，比如说“justify-self”🤔 好问题！不过答案是没有😅。但有一个已经存在的属性可以利用，那就是 auto margin ！我们可以用它控制指定元素在水平方向上的对齐方式。

<p><img src="auto-margins-horizontal.png" alt="Horizontal Alignment with Auto Margins" width="500"></p>

事实上，你也可以用 **auto margin** 控制指定元素在垂直方向上的对齐方式。

<p><img src="auto-margins-vertical.png" alt="Vertical Alignment with Auto Margins" width="500"></p>

而且，如果你在 Flex 项目设置了 `margin: auto`（相对于 left、right、top、bottom 四个方向都同时设置了），甚至可以实现 Flex 项目在容器中的垂直居中效果！

<p><img src="auto-margins-center.png" alt="Centering with Auto Margins" width="500"></p>

## 理解 margin

看到这儿，你可能有点困惑了。为什么使用了 `margin-left: auto` 后，Flex 项目被推倒右边了呢；为什么使用了 `margin-right: auto` 后，Flex 项目被推倒左边了呢。有点反直觉哦，别担心，我也这么觉得 😅

还记得 `margin` 的基本概念吗？其实就是为了给元素添加**间隔**。比如 `margin-left: 50px`，会在元素的左边添加 `50px` 的间隔，将元素向右推了一些距离。使用 `margin-left: auto`，`auto` 则会计算当前的整个可用空间，然后将这么多的空间安排在元素的左侧，结果将元素一直向右推。

<p><img src="understanding-margin.png" alt="Understanding Margin" width="500"></p>

| margin          | 间隔               | 表现         |
|-----------------|--------------------|-------------|
| `margin-left`   | 在左边添加间隔      | 将元素向右推 |
| `margin-right`  | 在右边添加间隔      | 将元素向左推 |
| `margin-top`    | 在上边添加间隔      | 将元素向下推 |
| `margin-bottom` | 在下边添加间隔      | 将元素向上推 |
| `margin`        | 在每个面都添加间隔  | 元素垂直居中 |


## Auto Margin 的优先级高 🏆

如果在 Flex 项目使用了 **auto margin**，那么它的优先级高于在其他地方设置的对齐属性，相当于在其他地方的设置无效了 💪

<p><img src="auto-margins-vs-flexbox.png" alt="Auto Margins vs Flexbox Properties" width="500"></p>

**为什么？**

> 注意：如果剩余空间分配给了 auto margin，那么对齐属性在那个维度上的设置就会无效，因为 `margin` 已经用完了剩余空间（在 Flex 项目分配完成后）。

如果用非开发术语表述的话，**auto margin** 是你怀着善意邀请的某个笨朋友，他住在你的房子里，然后认为整个房子都是他的，并占用了所有空间。你没有那种朋友？我也没有😳但我想你应该明白了我要表达的那个点了吧😂

## Auto Margin 案例

下面列出了一些关于使用 **auto margin** 的例子，非常亮眼！用它来布局你喜欢的导航栏排版样式非常好 🤩

<p><img src="auto-margins-examples.png" alt="Auto Margins Examples" width="500"></p>

## 我该用哪个？ 🤔

我保证你对使用哪个或者什么时候改用哪个有点头晕（这是要选择的问题，对嘛）😅。我是这么做的：

1. 优先使用 **Flexbox** 属性
2. 如果不能实现效果，就用 auto margin

理由？我觉得 Flexbox 属性更加符合直觉，比“auto margin” 的表达也更加明确。来比较下：

```css
.child {
  align-self: flex-end;
}
```

**vs**

```css
.child {
  margin-top: auto;
}
```

即使你没有学习过关于 Flexbox 方面的相关知识。只从字面上看代码的话，我们可以推断出 `child` 是对齐到*末端的（end）*。而来再看看 `margin-top: auto`，你可能就会有点头晕，它到底是想要实现怎样的布局效果。当然，这只是我的建议。你可以为你和你的团队做出合适的选择 😊

## 资源

- [W3C Flexbox Spec: Aligning with auto margins](https://www.w3.org/TR/css-flexbox-1/#auto-margins)
- [Hackernoon: Flexbox's Best-Kept Secret](https://hackernoon.com/flexbox-s-best-kept-secret-bd3d892826b6)
- [CSS Tricks: The peculiar magic of flexbox and auto margins](https://css-tricks.com/the-peculiar-magic-of-flexbox-and-auto-margins/)
- [Stack Overflow: Why are there no "justify-items" and "justify-self" properties?](https://stackoverflow.com/questions/32551291/in-css-flexbox-why-are-there-no-justify-items-and-justify-self-properties/33856609#33856609)
- [Stack Overflow: Can't scroll to top of flex item that is overflowing container](https://stackoverflow.com/questions/33454533/cant-scroll-to-top-of-flex-item-that-is-overflowing-container)
