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

### [第 12 天: justify-content [row]](#justify-content-row)

接下来要讲得这块就比较有趣了。`justify-content` 用来控制 Flex 项目在主轴上的对齐方式。本例中，主轴是水平的，即 `flex-direction` 置为 `row`。

这可能是我最常使用的容器属性了。你只要选择一个你喜欢的布局方式，Flexbox 会自动为你安排好。完全是响应式的。随着你拉伸、收缩窗口的宽度，Flexbox 会进行后台计算，保证你指定的布局一直有效。有点像是厨房里的电器——“设置好后，就不用管了” 🍗

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

### [第 13 天: justify-content [column]](#justify-content-column)

主轴方向也可以是垂直的。这种情况下，`flex-direction` 属性值为 `column`。下图中反应了此种情况下 Flex 项目的对齐方式。

<p><img src="code-tidbits/14-justify-content-column.png" alt="justify-content column" width="500"></p>

```css
.parent {
  flex-direction: column;
  
  justify-content: flex-start /* 默认 */
                or flex-end
                or center
                or space-around
                or space-between
                or space-evenly
}
```

<a id="space-around-vs-space-evenly"></a>

### [第 14 天: space-around vs space-evenly](#space-around-vs-space-evenly)

你可能不太容易区分 `space-around` 和 `space-evenly` 之间的细微差别。这里说下。对 `space-evenly` 来说，每个 Flex 项目两边的空间间隔都是一样的。而对于 `space-around`，项目与容器边缘的间隔是是项目间间隔的一半。后者给人的感受是，项目分布更加离散，好像它们更喜欢边缘生活一样 😂

<p><img src="code-tidbits/13-space-around-vs-space-evenly.png" alt="space-around vs space-evenly" width="500"></p>

<a id="align-items-row"></a>

### [第 15 天: align-items [row]](#align-items-row)

justify-content 控制的是项目在主轴上的布局方式。那么交叉轴上的布局，由谁控制呢？别担心，有 `align-items` 来负责。还记得吧，交叉轴方向始终是与主轴方向垂直的。就是说，如果主轴是水平的，即 flex-direction 为 row 的情况下，交叉轴则是垂直的。之前你有没有因为我们花了将近一个星期的时间来学习基础知识，而不高兴？好了，基础里讲的现在都派上用场了 🤓

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

### [第 16 天: baseline](#baseline)

`baseline` 这个值得需要解释一下。它与文本排版有关。是一个存在于文字之上的一个假想线。如果是一行相同字体大小的文字排在一起，你真的看不出有什么区别；如果需要将不同字体大小的文字排列在一起，如果不设置为 `baseline` （基于基线）显示，则可能出现文字显示位置上的混乱。为了确保所有不同大小的文本都位于一个统一基线的方法，就是使用 `baseline` 👍

<p><img src="code-tidbits/16-baseline.png" alt="baseline" width="500"></p>

<a id="align-items-column"></a>

### [第 17 天: align-items [column]](#align-items-column)

现在我们来看下如果交叉轴是水平的话， Flex 项目的对齐方式。也就是在 flex-direction 为 `column` 的情况。

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

### [第 18 天: align-content](#align-content)

还记得 `flex-wrap` 属性吧，允许多出来的 Flex 项目折行显示。而 `align-content` 属性就是控制这些 Flex 项目在交叉轴上的对齐方式的。此属性仅对折行项目生效，如果 Flex 项目仅有一行的话，设置此属性不会产生任何效果。

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

**[⬆ 回到顶部](#table-of-contents)**

## 项目属性

<a id="child-properties"></a>

### [第 19 天: 项目属性](#child-properties)

是的，我们已经讲完了应用在容器上的所有属性。现在我们开始讲述项目属性了。今天休息一下，明天我们再全速前进 🏎

<p><img src="code-tidbits/19-child-properties.png" alt="Child Properties" width="500"></p>

<a id="order"></a>

### [第 20 天: order](#order)

默认，Flex 项目的显示顺序与代码结构是一致的。但如何我们想要调整项目显示顺序的话，可以吗？当然，`order` 属性就是用来修改项目显示顺序的 🔢

<p><img src="code-tidbits/20-order.png" alt="order" width="500"></p>

```css
.child {
  order: 0 /* default */
      or <number>
}
```

<a id="flex-grow"></a>

### [第 21 天: flex-grow](#flex-grow)

我一开始提到过 Flexbox 对于响应式设计是非常友好的，这是它的亮点。`flex-grow` 属性允许 Flex 项目在必要时增长。因此，如果容器中有剩余空间，我们可以告诉某个特定的项目基于某种比例来填充它。真是太好了！当我刚学 CSS 的时候，记得一切都是静态的。有了这个属性，好像它就有了自己的大脑，能根据容器大小来调整自己的尺寸。我不需要监听尺寸变化了。因为项目自己会作出相应调整。对我来说这真是次洗礼 🤯

<p><img src="code-tidbits/21-flex-grow.png" alt="flex-grow" width="500"></p>

```css    
.child {
  flex-grow: 0 /* default */
          or <number>
}
```

<a id="flex-grow-calculation"></a>

### [第 22 天: flex-grow 的计算方法](#flex-grow-calculation)

自动增长填充剩余空间的功能非常酷。因为我们没有设置 Flex 项目的最终宽度，它的尺寸对我来说是有各种可能的。接下来我们来看看 flex-grow 的计算方法，当然讲这个的目的是为了搞懂魔法背后的秘密，帮助你更好地理解内部的执行机制。当然整个过程是由浏览器自动负责的，但对咱们来说不是什么魔法 😉

<p><img src="code-tidbits/22-flex-grow-calculation.png" alt="flex-grow calculation" width="500"></p>

<details>
  <summary><b>展开查看计算详情</b></summary><br>

I know it can be quite overwhelming to see all numbers crammed into a tidbit. So let's walk through the calculation 👍

我知道，看到所有的数字都塞进一个小玩意儿里，可能会让人不知所措。因此，我们下面做下解释 👍

下面是我们用到的 `HTML` 和 `CSS` 代码：

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

**第 1 步: 分解变量**

这里是公式:

```code
new width = ( (flex grow / total flex grow) x 剩余空间) + width
```

我们将公式里涉及到的变量填在下面的表格中：

变量  |     |
---        | --- |
flex grow  | *css 中设置*
total flex |  *需要计算*
剩余空间     | *需要计算*
width      | *css 中设置*

<br>

**第 2 步: 填入已知信息**

从 `CSS` 样式中，我们能得到：

- 每个子元素的宽度 width 是 `100`
- 父元素（容器）的宽度是 `700`
- 子元素的 `flex-grow` 属性值依次为 `1`、`0` 和 `3`

下面更新下表格信息：

<i></i>    |  Green | Yellow | Blue
---        | ---    | ---    | --- |
flex grow  | 1      | 0      | 3
total flex |
剩余空间 |
width      | 100    | 100    | 100

<br>

**第 3 步: 就散 "剩余空间"**

这是公式：

```code
剩余空间 = 父元素宽度 - 所有子元素宽度
```

我们已知：

- 每个子元素的宽度 width 是 `100`
- 父元素（容器）的宽度是 `700`

Great, we can use that information to calculate "total children widths":

```code
所有子元素宽度 = green + yellow + blue
             = 100   + 100    + 100

=> 300
```

现在能够计算咱们的“剩余空间”了：

```code
剩余空间 = 父元素宽度 - 所有子元素宽度
        = 700      -  300

=> 400
```

现在更新表格，添加如下这些额外信息：

<i></i>    |  Green | Yellow | Blue | Total
---        | ---    | ---    | ---  | --- |
flex grow  | 1      | 0      | 3
total flex |
剩余空间     | -      | -      | -    | **400**
width      | 100    | 100    | 100

<br>

**第 4 步: 计算 "total flex grow"**

这就比较简单啦，简单把设置的所有 `flex-grow` 属性值相加即可：

```code
total flex grow = green + yellow + blue
                = 1     + 0      + 3

=> 4
```

填写我们的表格。瞧！我们有了计算最终尺寸所需的全部信息 👍


<i></i>     |  Green | Yellow | Blue | Total
---         | ---    | ---    | ---  | --- |
flex grow   | 1      | 0      | 3    | **4**
free space  | -      | -      | -    | 400
width       | 100    | 100    | 100  |

<br>

**最后一步：计算 "new width"**

还记得公式吧：

```code
new width = ( (flex grow / total flex grow) x 剩余空间 + width
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

完成！我们成功计算出了新的宽度 🥳

<i></i>       |  Green   | Yellow  | Blue    | Total
---           | ---      | ---     | ---     | --- |
width         | 200      | 100     | 400  
flex grow     | 1        | 0       | 3       | 4
剩余空间    |          |         |         | 400
**new width** | **200**  | **100** | **400**  

<hr>

</details>

<a id="flex-shrink"></a>

### [第 23 天: flex-shrink](#flex-shrink)

使用 `flex-grow` 后，Flex 项目会自动扩展填充额外的空间。 `flex-shrink` 作用与此相反。当分配的空间不够怎么办？这个属性就是用来控制当可分配空间不足的情况下，每个 Flex 项目应该缩多少以便适应当前空间。需要注意的是，设置的数值越大，缩减的越多 👍

<p><img src="code-tidbits/23-flex-shrink.png" alt="flex-shrink" width="500"></p>

```css
.child {
  flex-shrink: 1 /* default */
            or <number>
}
```

<a id="flex-shrink-calculation"></a>

### [第 24 天: flex-shrink 的计算方法](#flex-shrink-calculation)

这是另一个可选的知识点。如果你像我一样好奇浏览器是如何计算 flex-shrink 的，那么跟我一起来看下吧 🐰

`flex-shrink` 背后的计算逻辑比 `flex-grow` 稍微复杂一点。你需要考虑到它的现有比例，并相应地收缩到 flex-shrink 的设置值。因此，需要更多的计算。再说一遍，如果这让你感到厌烦，那就跳过本节，这不是理解 Flexbox 必需的。而且浏览器都帮我们搞定了的，嘻嘻 😌

<p><img src="code-tidbits/24-flex-shrink-calculation.png" alt="flex-shrink calculation" width="500"></p>

<details>
  <summary><b>展开查看计算详情</b></summary><br>

实际上，计算是复杂一点的。不过不用担心，我们把它分解一下，一步一步来，搞明白它 💪

下面是我们用到的 `HTML` 和 `CSS` 代码：

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

**第 1 步: 分解变量**

这里是公式：

```code
new width = width - (shrink space x shrink ratio)
```

Let's extract the variables required in the formula to this handy table we can fill in as we go:

变量    |     |
---          | --- |
width        | *需要计算*
收缩空间 | *需要计算*
收缩率 | *需要计算*

<br>

**第 1 步: 填入已知信息**

From the `CSS` value, we can conclude the following:

从 `CSS` 样式中，我们能得到如下信息：

- 父元素（容器）宽度 `800`
- 绿色子元素宽度 `300`、`flex-shrink` 为 `4`
- 黄色子元素宽度 `600`、`flex-shrink` 为 `6`

接下来更新我们的表格数据：

<i></i>     |  Green | Yellow |
---         | ---    | ---    |
flex shrink | 4      | 6
width       | 300    | 600

<br>

**Step 3: 计算 "收缩空间"**

这是公式：

```code
收缩空间 = total children widths - parent width
```

还记得我们之前的信息吧：

- 父元素（容器）宽度 `800`
- 子元素宽度分别为 `300`、`600`

好的，我们用这些信息计算“total children widths”

```code
total children widths = green + yellow
                      = 300   + 600

=> 900
```

现在再来计算下“收缩空间”：

```code
收缩空间 = total children widths - parent width
        = 900                    -  800

=> 100
```

下面更新表格数据，添加额外信息：

<i></i>      |  Green | Yellow | Total
---          | ---    | ---    | --- |
flex shrink  | 4      | 6
width        | 300    | 600
收缩空间 | -      | -      | **100**

<br>

**第 4 步：计算 "收缩率"**

公式：

```code
收缩率 = (width x flex shrink) / total shrink scaled width
```

注意，我们引入一个新变量 `total shrink scaled width`，我们先来计算它。

<br>

**第 4.1 步：计算 "total shrink scaled width"**

公式：

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
