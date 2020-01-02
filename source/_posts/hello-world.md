---
title: Hello World
mathjax: true
---
Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).

<!--more-->

## Quick Start

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)

### Math

* 整行

$$sin^2\theta + cos^2\theta = 1$$

* 行内

这是一个行内公式： $sin^2\theta + cos^2\theta = 1$

* 测试用例

$$
\begin{aligned}
f_Y(y) & = f_X[h(y)]|h'(y)| \\[2ex]
& = f_X[h(y)]h'(y) \\[2ex]
& = \frac{1}{\theta}e^{-\frac{x}{\theta}}[\frac{dx}{dy}(-\frac{\theta}{ln(1-y)})] \\[2ex]
& = \frac{1}{\theta}e^{-\frac{-\frac{\theta}{ln(1-y)}}{\theta}}\frac{\theta}{1-y} \\[2ex]
& = \frac{1}{\theta}e^{ln(1-y)}\frac{\theta}{1-y} \\[2ex]
& = \frac{1-y}{\theta}\frac{\theta}{1-y} \\[2ex]
& = 1
\end{aligned}
\tag{1}
$$

$$
\frac{1}{\sigma} 
\tag{this is a test}
$$

### Tag Plugin

{% note default %}
#### Default Header
Welcome to [Hexo!](https://hexo.io)
{% endnote %}

{% note primary %}
#### Primary Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

{% note info %}
### Info Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

{% note success %}
#### Success Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

{% note warning %}
#### Warning Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

{% note danger %}
#### Danger Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

{% note info no-icon %}
#### No icon note
Note **without** icon: `note info no-icon`

note info, note info, note info
note info, note info, note info
note info, note info, note info
{% endnote %}

{% note success %}
#### Codeblock in note
{% code %}
code block in note tag
code block in note tag
code block in note tag
{% endcode %}
{% endnote %}

{% note default %}
#### Lists in note
* ul
* ul
  * ul
  * ul
* ul

1. ol
2. ol
  1. ol
  2. ol
3. ol
{% endnote %}

#### Table in Note

{% note default %}
| 1 | 2 |
| - | - |
| 3 | 4 |
| 5 | 6 |
| 7 | 8 |
{% endnote %}

#### Examples

{% tabs First unique name %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

#### Tabs with 3rd tab selected

{% tabs Second unique name, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

#### Tabs with no tab selected

{% tabs Third unique name, -1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

#### Tabs with custom labels

{% tabs Fourth unique name %}
<!-- tab Solution 1 -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab Solution 2 -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab Solution 3 -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

#### Tabs with icons only

{% tabs Fifth unique name %}
<!-- tab @text-width -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab @amazon -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab @bold -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

#### Tabs with icons and labels

{% tabs Sixth unique name %}
<!-- tab Solution 1@text-width -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab Solution 2 @amazon -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab Solution 3@bold -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

