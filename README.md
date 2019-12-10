# Flexbox30

30 天 30 个小知识点，学会 Flexbox 布局 ✨

<img src="flexbox30-cover.png" alt="Flexbox Cover" width="350">

<a id="table-of-contents"></a>

## 目录

1. [介绍](#flexbox-intro)
1. [Flex 容器 & Flex 项目](#flex-container-and-flex-items)
1. [直接子元素](#immediate-child-only)
1. [Flexbox 轴](#flexbox-axes)
1. [Flexbox 模块](#flexbox-module)
1. [Flex 容器属性](#parent-properties)
1. [Display](#display)
1. [block vs inline](#block-vs-inline)
1. [flex-direction](#flex-direction)
1. [flex-wrap](#flex-wrap)
1. [flex-flow](#flex-flow)
1. [justify-content [row]](#justify-content-row)
1. [justify-content [column]](#justify-content-column)
1. [space-around vs space-evenly](#space-around-vs-space-evenly)
1. [align-items [row]](#align-items-row)
1. [baseline](#baseline)
1. [align-items [column]](#align-items-column)
1. [align-content](#align-content)
1. [Flex 项目属性](#child-properties)
1. [order](#order)
1. [flex-grow](#flex-grow)
1. [flex-grow 的计算方法](#flex-grow-calculation)
1. [flex-shrink](#flex-shrink)
1. [flex-shrink 的计算方法](#flex-shrink-calculation)
1. [flex-basis](#flex-basis)
1. [flex-basis vs widths](#flex-basis-vs-widths)
1. [flex](#flex)
1. [align-self](#align-self)
1. [Flexbox 属性](#flexbox-properties)
1. [Flexbox Cheatsheet](#flexbox-cheatsheet)
1. [使用 auto margin 对齐](#auto-margins)
1. [资源](#resources)
1. [你好呀](#say-hello)
1. [下载 & 分享](#download-and-share)
1. [贡献](#contribution)
1. [License](#license)

## Flexbox 核心概念

<a id="flexbox-intro"></a>

### [第 1 天: 介绍](#flexbox-intro)

在 Flexbox 出现之前，我们主要使用浮动布局。对早期的 CSS 开发者来说，使用这种老旧方式带来的布局挫折和限制都心照不宣——特别是碰到在父元素中实现垂直居中的功能时。哎呀，烦死了！不过 Flexbox 的出现，让烦恼不再来！

<p><img src="code-tidbits/1-flexbox-intro.png" alt="Flexbox Introduction" width="500"></p>

<a id="flex-container-and-flex-items"></a>

### [第 2 天: Flex 容器 & Flex 项目](#flex-container-and-flex-items)

在开始学习 Flexbox 之前，我们先来搞清楚这个布局里会涉及到一种父子关系。我们称父元素为 Flex 容器，称子元素为 Flex 项目。

<p><img src="code-tidbits/2-flex-container-and-flex-items.png" alt="Flex Container & Flex Items" width="500"></p>

<a id="immediate-child-only"></a>

### [第 3 天: 直接子元素](#immediate-child-only)

有一件非常重要的、需要指出的事情是，Flex 项目是对 Flex 容器直接子元素的叫法。即 Flex 容器的作用范围是它的直接子元素，就这一层，不会更深了。也就是说 Flexbox 布局，反应地是父元素↔️直接子元素的关系！

当然，在所有具备父子关系的上下文环境里，你都可能创建 Flexbox 布局。当然 Flex 项目本身也可以是它孩子的 Flex 容器。注意，这里提到的两个容器不会互相干扰，不会有内部 Flex 容器覆盖外部 Flex 容器属性的事情发生。

这一个也许是帮助我理解 Flexbox 作用原理的最重要的一个概念了。知道了这个概念，帮我避免了好多“哎，为什么设置了就没用呢”的时刻发生 😅

<p><img src="code-tidbits/3-immediate-child-only.png" alt="Immediate Child Only" width="500"></p>

<a id="flexbox-axes"></a>

### [第 4 天: Flexbox 轴](#flexbox-axes)

Flexbox 布局会涉及到 2 根轴：主轴和交叉轴。主轴定义 Flex 容器中 Flex 项目的排版方向。交叉轴就比较简单了，它与主轴垂直。 

还记得数学课里学到的 **x** 轴 **y** 轴吧，不过跟这里可不一样。因为主轴方向可能是水平的，也可能是垂直的。**x** 轴上并不总是主轴。这是我犯过的一个错误，期望你不要重蹈覆辙啊 😅

<p><img src="code-tidbits/4-flexbox-axes.png" alt="Flexbox Axes" width="500"></p>

<a id="flexbox-module"></a>

### [第 5 天: Flexbox 模块](#flexbox-module)

现在再深入探讨下轴的知识。每个轴都有起始端和结束端。以主轴为例，起始位置叫“main start”，结束位置叫“main end”。交叉轴的“cross start”、“cross end”的概念于此类似。知道了轴的起始端和结束端概念，对后面学会如何控制 Flex 项目的排版很重要。

以上这些，就是 Flexbox 布局的基本知识了。

<p><img src="code-tidbits/5-flexbox-module.png" alt="Flexbox Module" width="500"></p>

**[⬆ 回到顶部](#table-of-contents)**

## 容器属性

<a id="parent-properties"></a>

### [第 6 天: 容器属性](#parent-properties)

现在我们知道了 Flexbox 布局是在父子关系中运行的。在这个系统里会涉及到两个实体。每个实体都单独拥有一套自己的 CSS 属性集合。这就是之前要区分 Flex 容器和 Flex 项目原因所在，因为它们各自都有不同的属性可供设置。下面我们从 Flex 容器属性开始讲起 🤰

<p><img src="code-tidbits/6-parent-properties.png" alt="Parent Properties" width="500"></p>

<a id="display"></a>

### [第 7 天: Display](#display)

首先，创建咱们的 Flex 容器。我们将父元素的 `display` 属性设置为 `flex` 就可以了。嘭！现在所有的直接子元素自动成为 Flex 项目了 🎊

一共有两种类型的 Flex 容器：`flex` 创建的是一个 *块* 级 Flex 容器。`inline-flex` 则会创建一个 *行内* 级别的 Flex 容器。更多关于 *block* 和 *inline* 的信息明天再说 😉

<p><img src="code-tidbits/7-display.png" alt="Display" width="500"></p>

```css
.parent {
  display: flex /* default */
        or inline-flex
}
```

<a id="block-vs-inline"></a>

### [第 8 天: block vs inline](#block-vs-inline)

简单地讲，`block` 元素占据整个容器的宽度。它们看起来就像是叠在一起的积木。而行内元素只占据它所需的空间。因此它们是一行排列的，一个挨着一个。

<p><img src="code-tidbits/8-block-vs-inline.png" alt="block vs inline" width="500"></p>

<a id="flex-direction"></a>

### [第 9 天: flex-direction](#flex-direction)

这个属性是用来定义主轴方向的。还记得我们讲过，主轴可以是水平也可以是垂直的吧。水平的主轴叫 **row**，垂直的主轴叫 **column**。而且，还有 **main start** 和 **main end** 的概念。我们简单添加一个 `reverse` 前缀就能将“main start”设置到反向位置。很酷吧 👍

<p><img src="code-tidbits/9-flex-direction.png" alt="flex-direction" width="500"></p>

```css
.parent {
  flex-direction: row /* default */
               or row-reverse
               or column
               or column-reverse
}
```

<a id="flex-wrap"></a>

### [第 10 天: flex-wrap](#flex-wrap)

Flex 项目默认会缩减自己的尺寸以便适应在一行内显示。也就是说，默认是 `nowrap` 的。然而，如果你需要保留它的尺寸，并且允许在容器内多行显示的话，那么就要考虑使用 `wrap` 了。

使用这个属性值后，允许 Flex 项目在一行显示不够的情况下，占据多行显示。

<p><img src="code-tidbits/10-flex-wrap.png" alt="flex-wrap" width="500"></p>

```css
.parent {
  flex-wrap: nowrap /* default */
          or wrap
          or wrap-reverse
}
```

<a id="flex-flow"></a>

### [第 11 天: flex-flow](#flex-flow)

其实这个属性你已经学过了。为什么这么说呢？因为它就是个简写属性，是 `flex-direction` 和 `flex-wrap` 两个属性的简写形式 👏

你可以用这个属性同时设置两个属性，或者只设置其中之一。默认值为 `row nowrap`。如果只设置了其中一个属性，那么另一个则保持默认设置。

<p><img src="code-tidbits/11-flex-flow.png" alt="flex-flow" width="500"></p>

```css
.parent {
  flex-flow: row nowrap /* default */
          or <flex-direction> <flex-wrap>
          or <flex-direction>
          or <flex-wrap>
}
```

<a id="justify-content-row"></a>

### [Day 12: justify-content [row]](#justify-content-row)

Here comes the fun part. This is the property that sets alignment along the main axis. In this example, the main axis lies horizontally. In other words, the flex-direction is set to `row`.

This is probably my most used parent property. You just choose the layout you like and BAM Flexbox automatically does it for you. And it's absolutely responsive. As your grow or shrink the window width, Flexbox will do the behind-the-scene calculation and ensure that your chosen layout is maintained. It's like one of those kitchen appliances where "you set it and forget it" 🍗

<p><img src="code-tidbits/12-justify-content-row.png" alt="justify-content row" width="500"></p>

```css
.parent {
  justify-content: flex-start /* default */
                or flex-end
                or center
                or space-around
                or space-between
                or space-evenly
}
```

<a id="justify-content-column"></a>

### [Day 13: justify-content [column]](#justify-content-column)

The main axis can also lie vertically. In that case, flex-direction is set to `column`. Here's how the flex items will be aligned in that instance.

<p><img src="code-tidbits/14-justify-content-column.png" alt="justify-content column" width="500"></p>

```css
.parent {
  flex-direction: column;
  
  justify-content: flex-start /* default */
                or flex-end
                or center
                or space-around
                or space-between
                or space-evenly
}
```

<a id="space-around-vs-space-evenly"></a>

### [Day 14: space-around vs space-evenly](#space-around-vs-space-evenly)

You might not notice the subtle difference between space-around and space-evenly. So let's talk about it. In `space-evenly`, the empty space in between the flex items is always equal. However, in `space-around`, only the inner items will have equal spacing in between each other. The first and last item will only be allocated half the spacing. Giving the visual appearance of it being more spread out. One may say these folks like to live life on the edge 😂

<p><img src="code-tidbits/13-space-around-vs-space-evenly.png" alt="space-around vs space-evenly" width="500"></p>

<a id="align-items-row"></a>

### [Day 15: align-items [row]](#align-items-row)

So justify-content controls how items are laid out on the main axis. What about their layout in the cross axis? Don't worry, that's where `align-items` come into play. Remember the cross axis is always perpendicular to the main axis. So if the main axis is sitting horizontally, where flex-direction is `row`. Then , the cross axis is sitting vertically. Aren't you glad we spend almost a week on the fundamentals, that knowledge is all being applied now 🤓

<p><img src="code-tidbits/15-align-items-row.png" alt="align-items row" width="500"></p>

```css
.parent {
  align-items: stretch /* default */
            or flex-start
            or flex-end
            or center
            or baseline
}
```

<a id="baseline"></a>

### [Day 16: baseline](#baseline)

The baseline value is a bit tricky. So let's make sure we understand what that is. Baseline has to do with typography or text. It is the imaginary line where the text sits. If you have the same font size, you really don't visually see a difference. However when you have different font sizes, then the text seems all over the place because the baseline is off. The way to ensure a uniform baseline where all the different sizes of text can rest on is to use the `baseline` value 👍

<p><img src="code-tidbits/16-baseline.png" alt="baseline" width="500"></p>

<a id="align-items-column"></a>

### [Day 17: align-items [column]](#align-items-column)

Now let's take a look at how our flex items are aligned if the cross axis is sitting horizontally. In other words, flex-direction is `column`.

<p><img src="code-tidbits/17-align-items-column.png" alt="align-items column" width="500"></p>

```css
.parent {
  flex-direction: column;
  
  align-items: stretch /* default */
            or flex-start
            or flex-end
            or center
            or baseline
}
```

<a id="align-content"></a>

### [Day 18: align-content](#align-content)

Remember we had `flex-wrap` where we allow flex items to wrap on separate lines. Well, with `align-content` we can control how those row of items are aligned on the cross axis. Since this is only for wrapped items, this property won't have any effect if you only have a singular line of flex items.

<p><img src="code-tidbits/18-align-content.png" alt="align-content" width="500"></p>

```css
.parent {
  align-content: stretch /* default */
              or flex-start
              or flex-end
              or center
              or space-between
              or space-around
}
```

**[⬆ back to top](#table-of-contents)**

## Child Properties

<a id="child-properties"></a>

### [Day 19: Child Properties](#child-properties)

Yay, you did it! We made it through the parent properties. Up next, let dig into the child properties. Take a breather today, tomorrow we go full speed again 🏎

<p><img src="code-tidbits/19-child-properties.png" alt="Child Properties" width="500"></p>

<a id="order"></a>

### [Day 20: order](#order)

By default, flex items are displayed in the same order they appear in your code. But what if you want to change that? No problem! Use the `order` property to change the ordering of your items 🔢

<p><img src="code-tidbits/20-order.png" alt="order" width="500"></p>

```css
.child {
  order: 0 /* default */
      or <number>
}
```

<a id="flex-grow"></a>

### [Day 21: flex-grow](#flex-grow)

I mentioned in the beginning that Flexbox is great for responsive design. This is where it shines. The `flex-grow` property allows our flex item to grow if necessary. So if there is extra free space in my container, I can tell a particular item to fill it up based on some proportion. That's pretty nuts! When I was learning CSS, I remember everything is pretty static. Now with this property, it's like it has its own brain and it will adjust its size depending on the container. That's so great. I don't have to monitor the size. It will adjust accordingly. This was a quite the mind blow for me 🤯

<p><img src="code-tidbits/21-flex-grow.png" alt="flex-grow" width="500"></p>

```css
.child {
  flex-grow: 0 /* default */
          or <number>
}
```

<a id="flex-grow-calculation"></a>

### [Day 22: flex-grow calculation](#flex-grow-calculation)

Being able to grow and fill the free space is pretty cool. Because we don't set the final width of our flex item, the size it grows to always seem so random to me. So let's look at the math. Honestly you don't need to know this to understand Flexbox. The browser takes care of this automatically for you. But knowing what's behind this sorcery might demystify this process and help you understand it better. It's like once you know the trick to the magic, you're no longer tricked by the magic 😉

<p><img src="code-tidbits/22-flex-grow-calculation.png" alt="flex-grow calculation" width="500"></p>

<details>
  <summary><b>Expand to see the calculation</b></summary><br>

I know it can be quite overwhelming to see all numbers crammed into a tidbit. So let's walk through the calculation 👍

Here's the `HTML` and `CSS` we're working with:

_HTML_

```html
<div class="parent">
  <div class="child green"></div>
  <div class="child yellow"></div>
  <div class="child blue"></div>
</div>
```

_CSS_

```css
.parent {
  width: 700px;
}
.child {
  width: 100px;
}
.green {
  flex-grow: 1;
}
.yellow {
  flex-grow: 0;
}
.blue {
  flex-grow: 3;
}
```

<br>

**Step 1: Breaking down the variables**

Here's the formula:

```code
new width = ( (flex grow / total flex grow) x free space) + width
```

Let's extract the variables required in the formula to this handy table we can fill in as we go:

Variables  |     |
---        | --- |
flex grow  | *provided from css*
total flex | *need to calculate*
free space | *need to calculate*
width      | *provided from css*

<br>

**Step 2: Fill in what we know**

From the `CSS` value, we can conclude the following:

- Each child element has a width `100`
- The parent element (container) has a width of `700`
- The child has a `flex-grow` of `1`, `0`, `3`

Let's update our chart with this information:

<i></i>    |  Green | Yellow | Blue
---        | ---    | ---    | --- |
flex grow  | 1      | 0      | 3
total flex |
free space |
width      | 100    | 100    | 100

<br>

**Step 3: Calculate "free space"**

This is the formula:

```code
free space = parent width - total children widths
```

Remember what we know:

- Each child element has a width `100`
- The parent element (container) has a width of `700`

Great, we can use that information to calculate "total children widths":

```code
total children widths = green + yellow + blue
                      = 100   + 100    + 100

=> 300
```

Now we can calculate our "free space":

```code
free space = parent width - total children widths
           = 700          -  300

=> 400
```

Let's update our chart and add these additional information:

<i></i>    |  Green | Yellow | Blue | Total
---        | ---    | ---    | ---  | --- |
flex grow  | 1      | 0      | 3
total flex |
free space | -      | -      | -    | **400**
width      | 100    | 100    | 100

<br>

**Step 4: Calculate "total flex grow"**

This is an easy one, we simply add up our total `flex-grow`:

```code
total flex grow = green + yellow + blue
                = 1     + 0      + 3

=> 4
```

Fill in our chart and Voilà! We have all the information we need for the final calculation 👍

<i></i>     |  Green | Yellow | Blue | Total
---         | ---    | ---    | ---  | --- |
flex grow   | 1      | 0      | 3    | **4**
free space  | -      | -      | -    | 400
width       | 100    | 100    | 100  |

<br>

**Final step: Calculate "new width"**

Remember the formula:

```code
new width = ( (flex grow / total flex grow) x free space) + width
```

_a. Green_

```code
new width = ( (1/4 * 400) ) + 100

=> 200
```

_b. Yellow_

```code
new width = ( (0/4 * 400) ) + 100

=> 100
```

_c. Blue_

```code
new width = ( (3/4 * 400) ) + 100

=> 400
```

Done! We have successfully calculated the new width 🥳

<i></i>       |  Green   | Yellow  | Blue    | Total
---           | ---      | ---     | ---     | --- |
width         | 200      | 100     | 400  
flex grow     | 1        | 0       | 3       | 4
free space    |          |         |         | 400
**new width** | **200**  | **100** | **400**  

<hr>

</details>

<a id="flex-shrink"></a>

### [Day 23: flex-shrink](#flex-shrink)

So `flex-grow` will expand to fill the extra space if there are any. The opposite of that is `flex-shrink`. What happens when you run out of space. This is the property that controls how much your flex items will shrink to fit. Note the larger the number, the more it will shrink 👍

<p><img src="code-tidbits/23-flex-shrink.png" alt="flex-shrink" width="500"></p>

```css
.child {
  flex-shrink: 1 /* default */
            or <number>
}
```

<a id="flex-shrink-calculation"></a>

### [Day 24: flex-shrink calculation](#flex-shrink-calculation)

This is another optional knowledge. But if you're like me and is curious how the browser calculates flex-shrink. Join me in this rabbit hole 🐰

The math behind `flex-shrink` is a bit more complicated then `flex-grow`. You need to take into account of it's existing proportion and shrink it accordingly to the flex shrink amount. Hence, a few more calculation involved. Again, if this is throwing you off. Skip it. You don't need to know this to understand Flexbox. Luckily the browser takes care of it for you, how wonderful 😌

<p><img src="code-tidbits/24-flex-shrink-calculation.png" alt="flex-shrink calculation" width="500"></p>

<details>
  <summary><b>Expand to see the calculation</b></summary><br>

Indeed the calculation is a bit more complicated. But no worries, let's break it down we go through it step by step, you got this 💪

Here's the `HTML` and `CSS` we're working with:

_HTML_

```html
<div class="parent">
  <div class="green"></div>
  <div class="yellow"></div>
</div>
```

_CSS_

```css
.parent {
  width: 800px;
}
.green {
  width: 300px;
  flex-shrink: 4;
}
.yellow {
  width: 600px;
  flex-shrink: 6;
}
```

<br>

**Step 1: Breaking down the variables**

This is the formula:

```code
new width = width - (shrink space x shrink ratio)
```

Let's extract the variables required in the formula to this handy table we can fill in as we go:

Variables    |     |
---          | --- |
width        | *need to calculate*
shrink space | *need to calculate*
shrink ratio | *need to calculate*

<br>

**Step 2: Fill in what we know**

From the `CSS` value, we can conclude the following:

- The parent element (container) has a width of `800`
- Green child element has a width `300` and `flex-shrink` of `4`
- Yellow child element has a width `600` and `flex-shrink` of `6`

Let's update our chart with this information:

<i></i>     |  Green | Yellow |
---         | ---    | ---    |
flex shrink | 4      | 6
width       | 300    | 600

<br>

**Step 3: Calculate "shrunk space"**

This is the formula:

```code
shrunk space = total children widths - parent width
```

Remember what we know:

- The parent element (container) has a width of `800`
- The child elements has a width of `300`, `600`

Great, we can use that information to calculate "total children widths":

```code
total children widths = green + yellow
                      = 300   + 600

=> 900
```

Now we can calculate our "shrunk space":

```code
shrunk space = total children widths - parent width
             = 900                   -  800

=> 100
```

Let's update our chart and add the additional information:

<i></i>      |  Green | Yellow | Total
---          | ---    | ---    | --- |
flex shrink  | 4      | 6
width        | 300    | 600
shrunk space | -      | -      | **100**

<br>

**Step 4: Calculate "shrink ratio"**

This is the formula:

```code
shrink ratio = (width x flex shrink) / total shrink scaled width
```

Notice this new variable, `total shrink scaled width`. So we need to calculate that first to get our shrink ratio.

<br>

**Step 4-1: Calculate "total shrink scaled width"**

This is the formula:

```code
total shrink scaled width = Σ(width x flex shrink)
```

"Σ" Sigma is a math symbol that means the summation of something. So we need to apply `width x flex shrink` for all the child elements.

_Green_

```code
width x flex shrink = 300 x 4

=> 1200
```

_Yellow_

```code
width x flex shrink = 600 x 6

=> 3600
```

_Finally_

```code
total shrink scaled width = 1200 + 3600

=> 4800
```

Let's add this information to our chart:

<i></i>                   |  Green | Yellow | Total
---                       | ---    | ---    | --- |
flex shrink               | 4      | 6
width                     | 300    | 600
shrunk space              | -      | -      | 100
total shrink scaled width | -      | -      | **4800**

<br>

**Step 4-2: Back to calculating "shrink ratio"**

Fantastic, now that we know the "total shrink scaled width", we can return with calculating the "shrink ratio". Remember the formula:

```code
shrink ratio = (width x flex shrink) / total shrink scaled width
```

_Green_

```code
shrink ratio = (300 x 4) / 4800

=> 0.25
```

_Yellow_

```code
shrink ratio = (600 x 6) / 4800

=> 0.75
```

Let's add this information to our chart:

<i></i>      |  Green   | Yellow   | Total
---          | ---      | ---      | --- |
flex shrink  | 4        | 6
width        | 300      | 600
shrunk space | -        | -        | 100
shrink ratio | **0.25** | **0.75**

<br>

**Final step: Calculate "new width"**

Remember the formula:

```code
new width = width - (shrink space x shrink ratio)
```

_Green_

```code
new width = 300 - (100 x 0.25)

=> 275
```

_Yellow_

```code
new width = 600 - (100 x 0.75)

=> 525
```

Done! We have successfully calculated the new width 🥳

<i></i>       |  Green   | Yellow
---           | ---      | ---     |
width         | 300      | 600
shrunk space  | 4        | 6
shrink ratio  | 0.25     | 0.75
**new width** | **275**  | **525**

<hr>
</details>

<a id="flex-basis"></a>

### [Day 25: flex-basis](#flex-basis)

With the flex-grow and flex-shrink property, we know the flex size changes. With the `flex-basis` property, this is where we set its initial size. You can think of this property as the width of our flex items. So your next question might be what's the difference between width and flex-basis. Of course, you can still use width and it will still work. The reason it works is because if you didn't set the flex-basis, it will default to the width. So your browser will always try to find the `flex-basis` value as the size indicator. And if it can't find it, then it has no choice but to go with your width property.  Don't make the browser do extra work. Do it the proper flex way and use `flex-basis`.

You may notice I referenced width in my previous formulas. That's because I had not cover flex-basis at that point. So if we want to be **flex** correct, please replace where I mentioned width with flex-basis 😝

<p><img src="code-tidbits/25-flex-basis.png" alt="flex-basis" width="500"></p>

```css
.child {
  flex-basis: auto /* default */
           or <width>
}
```

Valid width values are absolute [`<length>`](https://developer.mozilla.org/en-US/docs/Web/CSS/length) and [`<percentage>`](https://developer.mozilla.org/en-US/docs/Web/CSS/percentage). You can see some examples and read more on MDN web docs:

- [`MDN: <length>`](https://developer.mozilla.org/en-US/docs/Web/CSS/length)
- [`MDN: <percentage>`](https://developer.mozilla.org/en-US/docs/Web/CSS/percentage)

<a id="flex-basis-vs-widths"></a>

### [Day 26: flex-basis vs widths](#flex-basis-vs-widths)

Here you can see very clearly that when an item has a flex-basis and a width. The browser will always use the value set with `flex-basis` . Again, another reason to use the proper flex way 😉

But watch out, if you also set a `min-width` and `max-width`. In those cases, `flex-basis` will lose and will not be used as the width.

<p><img src="code-tidbits/26-flex-basis-vs-widths.png" alt="flex-basis vs widths" width="500"></p>

<a id="flex"></a>

### [Day 27: flex](#flex)

Sometimes, setting `flex-grow`, `flex-shrink` and `flex-basis` separately are tiring. Well, don't you worry. For the lazy programmers, I mean the efficient programmers 😜  You can set all 3 with the `flex` shorthand. The added bonus of this way is you don't have to set all 3 value, you can skip the properties you're not interested in and just set the one you are. And for the ones you skipped, it will just take on the default value. Awesome 👍

<p><img src="code-tidbits/27-flex.png" alt="flex" width="500"></p>

```css
.child {
  flex: 0 1 auto /* default */
     or <flex-grow> <flex-shrink> <flex-basis>
     or <flex-grow>
     or <flex-basis>
     or <flex-grow> <flex-basis>
     or <flex-grow> <flex-shrink>
}
```

<a id="align-self"></a>

### [Day 28: align-self](#align-self)

Remember our `align-items` property where we can set the flex item along the cross axis. The thing with `align-items` is that it forces ALL of the flex items to play with the rules. But what if you want one of them to break the rule. No worries, for  you independent thinkers, you can use `align-self`. This property accepts all of the same values given to `align-items`, so you can easily break from the pack 😎

<p><img src="code-tidbits/28-align-self.png" alt="align-self" width="500"></p>

```css
.child-1 {
  align-self: stretch /* default */
           or flex-start
           or flex-end
           or center
           or baseline
}
```

## Summary

<a id="flexbox-properties"></a>

### [Day 29: Flexbox Properties](#flexbox-properties)

YAY!!! You did it! You learned all the properties of Flexbox! You're a Flexbox ninja now! We covered a lot in this short amount of time. Go back and re-visit the ones you still don't understand. Don't just read my Flexbox lessons. Check out other Flexbox tutorials. Sometimes reading a different perspective will help solidify your knowledge and fill in any gaps. Remember the best way to get better is to apply. I gave you the knowledge, now it's on YOU to apply and build something with it 💪

<p><img src="code-tidbits/29-flexbox-properties.png" alt="Flexbox Properties" width="500"></p>

<a id="flexbox-cheatsheet"></a>

### [第 30 天: Flexbox 备忘单](#flexbox-cheatsheet)

Final tidbit! Let me give you one more tidbit for the road. Memorizing all the available properties is not easy. Even after doing creating this entire tutorial, I still don't have all these properties memorized. Being a good programmer is not about how much you memorize, it's about problem solving. And that's why it's important for a programmer to continue to stay humble and learn. It's all about expanding our toolkit so when we do face a problem, we have a variety of tools that we can select from to fix it 🧰

恭喜你完成了 Flexbox30 项目！我希望你收获很多，谢谢你让我的 tidbits 成为你编程旅程的一部分 💛

<p><img src="code-tidbits/30-flexbox-cheatsheet.png" alt="Flexbox Cheatsheet" width="500"></p>

**[⬆ 回到顶部](#table-of-contents)**

<a id="auto-margins"></a>

### [福利: 使用 auto margin 对齐](#auto-margins)

Bonus content! Another way to align Flexbox child elements is to use auto margins. Although this isn't a Flexbox property, it's still important to be aware of it because it has a very interesting relationship with Flexbox. Check out my code notes on it if you're interested  👉 [Flexbox: Aligning with Auto Margins](/flexbox-aligning-with-auto-margins/README.md)



<p><img src="code-tidbits/bonus-auto-margins.png" alt="Flexbox Cheatsheet" width="500"></p>

<a id="resources"></a>

## 📚 资源

**学习 Flexbox**

- [MDN web 文档: Flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)
- [MDN web 文档: Flexbox 的基本概念](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
- [CSS-Tricks: A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Yoksel: Flex Cheatsheet](https://yoksel.github.io/flex-cheatsheet/)
- [JoniBologna.com: Flexbox Cheatsheet](http://jonibologna.com/flexbox-cheatsheet/)
- [Interneting is hard: Flexbox](https://internetingishard.com/html-and-css/flexbox/)

**官方规范**

- [W3C: Flexbox](https://www.w3.org/TR/css-flexbox-1/)

**社区建议**

- [Flexbox Zombies](https://flexboxzombies.com) $
- [Flexbox Froggy](https://flexboxfroggy.com/)
- [Wes Bos: What the Flexbox?!](https://flexbox.io/)

<a id="say-hello"></a>

## 👋 你好呀

> I share JS, HTML, CSS tidbits every week!

Twitter: [@samantha_ming](https://twitter.com/samantha_ming)  
Instagram: [@samanthaming](https://www.instagram.com/SamanthaMing/)  
Facebook: [@hi.samanthaming](https://www.facebook.com/hi.samanthaming/)  
Medium: [@samanthaming](https://medium.com/@samanthaming)  
Dev: [@samanthaming](https://dev.to/samanthaming)  
Official: [samanthaming.com](https://www.samanthaming.com/)

<a id="download-and-share"></a>

## 💖 下载 & 分享

Absolutely! You are more than welcome to download and share my code tidbits. If you've gotten any value from my content and would like to help me reach more people, please do share!

One thing that I kindly ask is that you don't edit the images or crop my name out. Please leave the images intact. Thank you for choosing to do the right thing 😇

<a id="contribution"></a>

## 🌟 贡献

Yes! Anyone is welcome to contribute to the quality of this content. Please feel free to submit a PR request for typo fixes, spelling corrections, explanation improvements, etc. If you want to help translate the tutorial, that's even cooler! I'm hoping to at least create a Chinese version soon 👩🏻‍🏫

**[⬆ back to top](#table-of-contents)**

<a id="license"></a>

## 👩🏻‍⚖️ License

Thank you for wanting to share and include my work in your project 😊 If you're wondering how to provide attributions. It simply means don't edit the images. There is attribution automatically built into them. Easy peasy right! So you don't have to provide additional attribution when you share the images ⭐️

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.

**[⬆ back to top](#table-of-contents)**
