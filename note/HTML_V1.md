# HTML学习/复习笔记🤗
- **创建日期：** 2025/06/07
- **创建目的：** 学习和巩固HTML标签的简单使用和进阶运用
- **版本：** V1

## HTML常用标签列表
- [基本结构标签](#基本结构标签)
    - [`<html> 根标签`](#html根标签)
## 基本结构标签
### `<html>`根标签
- `<html>`是整个HTML页面的容器,所有其他HTMl内容都必须包含在`<html>`标签内

```html
<html>
    <!-- 页面其他内容 -->
</html>
```

**可用属性**
- **`lang`**（指定语言）
    - **语言代码：** 如 en（英语）、zh（中文）、es（西班牙语）。
    - **地区代码（可选）：** 如 US（美国）、CN（中国）、TW（台湾）

    ⚠️**未指定语言的情况：**
    - **默认行为：** 浏览器优先使用服务器头 Content-Language，其次可能使用用户界面语言，但不准确
    - **建议：** 始终为HTML文档设置`<lang>`属性，以确保文档正常运行。
    ```html
    <html lang="语言代码">
    <html lang="zh"> <!-- 中文 -->
    <html lang="zh-TW"> <!-- 繁体中文（台湾） -->
    <html lang="en"> <!-- 英语 -->
    ```

    - **样式控制：** CSS 可通过` :lang() `伪类选择特定语言的元素：
    ```css
    :lang(zh) { 
        font-family: "SimSun", serif; 
    }
    ```
    - **多语言文档：** 如果文档包含多种语言，可以在子元素中覆盖` lang `属性
    ```html
    <html lang="en">
        <body>
            <p>English paragraph.</p>
            <p lang="zh-CN">中文段落。</p>
        </body>
    </html>
    ```
    - **动态语言切换：**  通过 JavaScript 动态修改` lang `属性：
    ```javascript
    document.documentElement.lang = 'zh-CN';
    ```
- **`dir`** （文本方向）
    - **`ltr`（默认）：** 从左到右（如英语、中文）。
    - **`rtl`：** 从右到左（如阿拉伯语、希伯来语）。
    ```html
    <html lang="ar" dir="rtl"> <!-- 更改文本方向为从右到左 -->
    ```
    - **样式控制：** 在CSS中可以通过`[dir="rtl"]`定义特定方向文字的样式
    ```css
    [dir="rtl"] {
        text-align: right;
    }
    ```
- `<html>`标签同时支持所有**全局属性**如`class`,`id`,`style`。

⚠️ `<!DOCTYPE html>`为**文档类型声明**（Document Type Declaration），并非`<html>`标签，用于告诉浏览器当前文档使用的是HTML5标准。详情前往[`<!DOCTYPE html>`](#)

### `<head>` 元数据
- `<head>`标签包含这个HTML文档的**元数据**（metadata），元数据不会直接显示为页面内容，而是会影响浏览器的**渲染**，**抓取**，以及外部资源的**加载**。
- **位置：** 必须位于[`<html>`](#html根标签)标签内，并且在[`<body>`](#body-内容标签)标签之前。
```html
    <!DOCTYPE html>
    <html>
        <head>
            <!--元数据（metadata）具体看下面的子标签-->
        </head>
    </html>
```
- **子标签（元数据类型）**
    #### `<title>` 标题
    - 定义网页标题（显示在浏览器标签页和搜索引擎结果中）
    ```html
        <!--必须包含在<head>标签内-->
        <title>网站标题</title>
    ```
    #### `<meta>` 元数据
    **字符集声明** `charset`

    ```html
        <meta charset="UTF-8">
    ```
    - 指定文档的字符编码为UTF-8 -可变长编码（1-4字节），兼容ASCII，覆盖Unicode所有字符 （常用于现代网页的开发）
    - **位置:** 最好放置在`<head>`标签内的前部，确保最先运行保证浏览器可以正确解析文本。  

    **视口移动** `viewport`   

    - **核心目标**：   
    1. 确保网页在不同设备上的正确显示（响应式布局）。
    2. 避免页面缩放导致内容遮挡造成阅读以及操作困难。
    3. 视频特殊分辨率显示器以及屏幕（部分高分辨率屏幕以及刘海屏等）
    ```html
        <meta name="viewport">
    ```
    - **参数：**`width=device-width`   
    **作用：**   将视口宽度设置为设备的物理屏幕宽度（以 CSS 像素为单位）。  
    **重要性：** 确保CSS媒体查询功能（比如`@media (max-width:768px)`）可以正常工作。
    避免移动端浏览器以桌面宽度渲染页面，导致内容过小以及排版混乱。
    ```html
        <meta name="viewport" content="width=device-width"> s
    ```
    - **参数：**`initial-scale=1.0`   
    **作用：** 设置页面首次加载时的缩放比例为1.0（100%缩放）。   
    **效果：** 用户无需手动缩放就可以查看到完整的网站内容。防止浏览器自动调整缩放比例   
    **重要性：** 如未设置这项参数，部分设备以及浏览器可能会进行默认缩放，比如iPhone上的Safari浏览器的默认缩放为0.8。
    ```html
        <!--基础响应式设置（推荐）-->
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    ```
    - **参数：** `maximum-scale=1.0` / `minimum-scale=1.0`
    **作用：** 限制用户手动缩放的最大和最小比例。
    ```html
    <!--允许用户缩放的设置-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
    ```
    - **参数：** `user-scalable=no`    
    **作用：** 禁止用户手动缩放页面。  
    **适用场景：** 全屏交互式应用（如地图，绘图工具等），需要严格控制UI布局的场景（如电子书阅读器等）
    - iOS以及Android最新版本以及逐步限制此功能以提升可访问性。
    ```html
    <!--禁止用户缩放的严格设置-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    ```

-**注意事项**
1. **始终定义** `width=device-width`
    - 避免移动端浏览器以桌面宽度渲染页面导致。
2. **测试不同设备**
    - 使用Chrome DevTools中的设备模式或真机测试。
3. **处理刘海屏**
    ```html
    <!--处理刘海屏设备-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    ```
    ```css
    body {
        /*使用CSS环境变量避开刘海屏区域*/
        padding-top: env(safe-area-inset-top);
        padding-bottom: env(safe-area-inset-bottom);
        padding-left: env(safe-area-inset-left);
        padding-right: env(safe-area-inset-right);
    }
    ```
#### **SEO相关`meta`元数据标签**
这些标签影响搜索引擎对页面的理解和展示。
```html
<!--页面描述 - 显示在搜索结果摘要中-->
<meta name="description" content="这是一个关于HTML的笔记，介绍了<html>,<head>，<body>等常用标签，适合前端开发者学习研究">

<!--关键此(在现代SEO中权重较低)-->
<meta name="keywords" content="HTML,meta标签，前端开发，笔记，响应式开发">

<!--作者信息-->
<meta name="author" content="Jiamin YU">

<!--版权信息-->
<meta nema="copyright" content="© 2023 我的网站">

<!--页面分类/主题-->
<meta name="subject" content="前端开发笔记">

<!--页面等级（内容分级）-->
<meta name="rating" content="General">

<!--搜索引擎爬虫控制-->
<meta name="robots" content="index,follow"><!--允许索引和跟踪链接-->
<meta name="robots" content="noindex,nofollow"><!--禁止索引和跟踪链接-->
```

#### **社交媒体`<meta>`元标签 (Open Graph)**
这些标签控制页面在社交媒体平台(facebook,微信,微博等)上的分享展示效果
- Open Graph协议由Facebook创建，现已成为社交媒体分享的标准协议，被微信、微博、LinkedIn等众多平台支持。    
**核心标签：**
```html
    <!--页面标签（必需！）-->
    <meta property="og:title" content="前端开发指南-从入门到精通">

    <!--页面类型（必需！）-->
    <meta property="op:type" content="article">
    <!--常用类型website，artice，video.other等。适用与大多数场景-->

    <!--页面图片（必需！）-->
    <meta property="og:image" content="图片URL">

    <!--页面URL（必需！）-->
    <meta property="og:url" content="页面URL">

    <!--页面描述-->
    <meta property="og:description" content="包含HTML的完整开发学习路径，包含项目实践以及实战。">

    <!--网站名称-->
    <meta property="og:site_name" content="前端开发学院">

    <!--网站语言-->
    <meta property="og:locale" content="zh-CN">

```
- 这些仅包含部分核心常用标签，更多标签前往[open graph protocol](https://ogp.me/)(外部网站)进行查看。
#### `<link>`外部资源链接
-- `<link>`用于**链接外部资源**，常用于引入CSS样式表，也可以用于其他资源关系声明。
```HTML
<link rel="stylesheet" href="styles.css">
```
**`rel`属性详细说明**    

-- `rel="stylesheet"`-css样式表链接
```html
    <!--基础样式表链接-->
    <link rel="stylesheet" href="main.css">
    <!--媒体查询样式表链接-->
    <link rel="stylesheet" href="print.css" media="print">
    <link rel="stylesheet" href="mobile.css" media="screen and (max-width: 768px)">
```
- **作用：** 引入CSS样式表
- **加载方式：** 阻塞渲染，直到CSS加载完成
- **媒体查询：** 可以指定在特定条件下加载

-- **`rel="icon` 网站图标**
```html
    <!--传统favicon-->
    <link rel="icon" href="favion.ico" type="image/x-icon">

    <!--现代PNG格式-->
    <link rel="icon" href="favion-32x32.png" type="image/png" sizes="32x32">
    <link rel="icon" href="favion-16x16.png" type="image/png" sizes="16x16">

    <!--移动设备图标-->
    <link rel="apple-touch-icon" href="apple-touch-icon.png">
    <link rel="apple-touch-icon" href="apple-touch-icon-180x180.png" sizes="180x180">

    <!--安卓/Chrome图标-->
    <link rel="manifest" href="/mainfest.json">

```
- **显示位置：** 浏览器标签页，书签，桌面快捷方式
- **尺寸建议：** 提供多种尺寸适应不同场景
- **格式建议：** PNG优于ICO，支持透明度调节等
-- **`rel="preload" 资源预加载`**
```html
    <!--预加载关键CSS-->
    <link rel="preload" href="main.css" as="style" onload="this.onload=null;this.rel='stylesheet'">

    <!--预加载字体-->
    <link rel="preload" href="font.wooff2" as="font" type="font/wooff2" crossorigin>
```
-- **`rel="dns-prefetch"` 和 `rel="preconnect"` - 网络优化**
```html
    <!--DNS预解析-->
    <link rel="dns-prefetch" href="//fonts.googleapis.com">
    <link rel="dns-prefetch" href="//api.example.com">

    <!--预链接（包括DNS解析，TCP握手，TLS协商）-->
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link rel="preconnect" href="https://api.example.com">
```
- **dns-prefetch：** 仅进行DNS解析，适用于可能用到的第三方域名
- **preconnect：** 建立完整连接，适用于确定需要使用到的关键第三方资源
- **性能提升：** 减少后续请求的连接建立时间

### `<script>` 脚本标签
- `<script>`标签用于在HTML中嵌入或者引用JavaScript代码。
```html
<!--内联JavaScript脚本-->
<script>
    console.log(`页面加载完成`;
    document.addEventListener('DOMContentLoaded',function(){
        console.log('DOM构建完成');
    });
</script>
```
- **加载引用JavaScript脚本代码**
    
    默认行为（阻塞加载）：
    ```html
    <script src="blocking.js"></script>
    ```
    - **行为：** 立即开始下载并执行，阻塞HTML解析
    - **适用：** 页面以来的关键脚本
    - **缺点：** 可能增加页面渲染时间

    `async`异步加载：
    ```html
    <script src="analytics.js" async></script>
    ```
    - **行为：** 并行下载，下载完成后立即执行
    - **执行时机：** 不确定，可能在DOM构建完成前执行
    - **适用：** 独立的第三方脚本（统计，广告等）

    `defer`延迟执行：
    ```html
    <script src="app.js" defer></script>
    ```
    - **行为：** 并行下载，等DOM构建完成后按顺序执行
    - **执行时机：** DOMContentLoaded事件前
    - **适用：** 需要操作DOM的脚本

### `<styles>` 内部样式
`<styles>`标签用于在HTML文档内部直接定义CSS样式
- **位置:** 通常放在[`<head>`](#head-元数据)标签内部
- **作用范围：** 当前HTML文档
- **优先级：** 高于外部CSS样式表，低于内联样式
- **使用场景：** 页面特定样式，关键CSS优化
```html
<!-- 关键路径CSS内联 -->
<style>
    /* 首屏关键样式，加快首次渲染 */
    body { margin: 0; font-family: sans-serif; }
    .header { background: #333; color: white; height: 60px; }
    .hero { height: 400px; background: url('hero.jpg'); }
</style>

<!-- 非关键CSS异步加载 -->
<link rel="preload" href="full-styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<!--用户禁用JavaScript的后备方案，使用传统同步加载CSS-->
<noscript><link rel="stylesheet" href="full-styles.css"></noscript>
```
### `<body>` 内容标签 
`<body>`内容标签包含HTMl文档中所有可见内容，是用户在浏览器中实际看到的和交互的部分

```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>示例页面</title>
</head>
<body>
    <!-- 所有用户可见和可交互的内容都放在这里 -->
    <header>
    </header>
    
    <main>
        <article>
            <h2>文章标题</h2>
            <p>文章内容...</p>
        </article>
    </main>
    
    <footer>
        <p>版权信息</p>
    </footer>
</body>
</html>
```

- **唯一性：** 每个HTML文档**只能有一个`<body>`标签**
- **内容类型：** 包含所有网页的可见元素，如文本，图片，视频，表单等
- **事件处理：** 可以绑定页面级别的JavaScript事件
- **样式应用：** 是CSS演示的主要应用容器

**常用事件属性：**
```html
<body onload="pageLoaded()" 
      onresize="handleResize()" 
      onscroll="handleScroll()"
      onbeforeunload="confirmLeave(event)">
    
    <script>
        function pageLoaded() {
            console.log('页面完全加载完成（包括图片、样式等）');
        }
        
        function handleResize() {
            console.log('窗口大小发生变化');
            // 响应式布局调整
        }
        
        function handleScroll() {
            console.log('页面滚动中');
            // 滚动特效、懒加载触发等
        }
        
        function confirmLeave(event) {
            event.preventDefault();
            event.returnValue = '确定要离开此页面吗？';
            return '确定要离开此页面吗？';
        }
    </script>
</body>
```
**`onload="方法()"`**    
- **触发时机：** 所有资源完成加载（HTML，CSS，JavaScript，图片，字体等资源）
- 比`DOMContentLoaded`更晚触发
- 整个页面完成渲染后执行，在**首次加载，刷新页面，从其他页面导航**时触发

**`onresize="方法()"`**
- **触发时机：** 浏览器窗口大小改变时触发
- 移动设备旋转屏幕
- 打开或者关闭网页端开发者工具
- 用户进行缩放页面操作时
- **功能实现：** 响应式布局响应，缩放时对页面进行重新布局等等

！高频触发事件，需要进行防抖处理 

**`onscroll="方法()`**
- **触发时机：** 用户滚动页面，包括鼠标滚轮，键盘，触摸等
- 程序调用`scrollTo()`和`scrollBy()`方法触发页面滚动
- 点击锚点链接跳转页面时
- 浏览器前进/后退恢复滚动位置时
- **功能实现：** 导航栏的固定和隐藏，无限滚动加载，视差滚动效果，元素进入动画，阅读进度条等等

！极高频事件-必需优化性能

**`onbeforeunload="方法()"`**
- **触发时机：** 关闭浏览器标签页/窗口时
- 刷新页面(F5,Ctrl+R)
- 导航到其他页面
- 表单提交到其他页面
- 程序调用`window。location`跳转时
- **应用场景：** 表单数据保护和更新

！**限制：** 现代浏览器不允许自定义提示框文本，仅支持显示浏览器默认的确认对话框

### `<!DOCTYPE html>` 文档类型说明

- `<!DOCTYPE html>`作为HTML文档的**第一行代码**，必须出现在所有HTML标签之前。
```html
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <title>Document</title>
        </head>
        <body>
            <p>基础HTML格式</P>
        </body>
    </html>
```
- **核心功能** 声明文档类型  
    告知浏览器当前使用的HTML标准(如 HTML5，HTML4.01，XHTML等)[跳转到HTML标准](#html标准)
## 文本内容标签
文本内容标签需要包含在[`<body>`](#body-内容标签)标签内。

### 标题标签 `h1` - `h6`
HTML提供了六个级别的标题标签(`h1` - `h6`)，用于建立文档的层次结构，这对[SEO](#seo相关meta元数据标签)和可访问性都非常重要。

```html
<!-- 标题层次结构示例 -->
<h1>网站主标题（每页只能有一个）</h1>
    <h2>第一个主要章节</h2>
        <h3>第一个子章节</h3>
            <h4>详细内容标题</h4>
                <h5>更具体的标题</h5>
                    <h6>最小级别标题</h6>
        <h3>第二个子章节</h3>
    <h2>第二个主要章节</h2>
        <h3>另一个子章节</h3>
```
- **SEO权重：** 标题级别越高在搜索引擎中的权重越高

### `<p>`/`<br>`段落与换行
#### `<p>`段落标签
```html
<p>这是一个标准段落。段落标签会自动在前后添加间距，将相关的文本内容组织在一起。每个段落代表一个完整的思想或概念。</p>

<p>这是另一个段落。浏览器会自动在段落之间添加垂直间距，使内容更易读。段落内的文本会自动换行以适应容器宽度。</p>

<!-- 段落中可以包含其他内联元素 -->
<p>段落中可以包含<strong>强调文本</strong>、<a href="#">链接</a>、<em>斜体文本</em>等内联元素。</p>
```
- **作用：** 将相关文本阻止成逻辑段落
- **默认样式：** 块级元素，有默认间距（通常为1em）
- **自动换行：** 文本会自动适应容器宽度
- **内联元素** 可以在元素内包含[文本格式化标签](#文本格式化标签)等等标签



### 文本格式化标签
---
## HTML标准
1. HTML5
    ```html
    <!DOCTYPE html>
    ```
    - **适用场景：** 现代网页，单页应用（SPA），跨平台开发（如React，Vue）。
    - **优势：**  丰富的标签，原生支持图片视频音频等等。
2. XHTML
    ```html
    <!--XHTML 1.0 Strict-->
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

    <!-- XHTML 1.0 Transitional-->
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

    ```
    - **适用场景：** 遗留企业系统、需要 XML 校验的环境（如某些银行或政府项目）。
    - **劣势：** 严格的语法要求（如必须闭合标签）导致开发效率低，且现代浏览器已不再强制要求。
3. XML/XHTML5
    ```html
    <!--与 HTML5 相同的 DOCTYPE，但文档必须符合 XML 语法-->
    <!--服务器设置 Content-Type: application/xhtml+xml-->
    <!DOCTYPE html>
    ```
    - **适用场景：** 后端数据处理（如 XML 数据源生成 HTML 页面）、工具链集成（如 XSLT 转换）。
4. HTML4.01  
    没有用，就不写DOCTYPE声明语句了。
    - **适用场景：** 仅保留用于维护老旧网站或年代久远的历史文档。
## SEO(Search Engine Optimization) 搜索引擎优化
前端开发中，SEO指的是通过优化网页结构，内容和代码，让搜索引擎（如百度，谷歌google等）更好的理解，索引和排名你的网站，从而提高网站在搜索引擎搜索结果中的可见性和排名。
- **前端SEO的主要方法**   
**HTML结构优化**
    - 使用正确的HTML语义化标签（如`<header>`,`<nav>`,`<main>`,`<article>`等）
    - 正确使用标题标签层级（H1，H2，H3等）
    - 添加适合的元数据meta标签（title，describtion，keywords）   
**内容优化**
    - 确保页面有高质量原创内容
    - 使用相关的关键词，自然的融入内容中
    - 图片添加alt属性进行描述
**技术优化**
    - 提高页面加载速度
    - 确保网站面向移动端友好（响应式设计）
    - 使用HTTPS协议
    - 创建XML网站地图
    - 优化URL结构，使其简洁明了    
**用户体验优化**
    - 降低跳出率
    - 提高页面停留时间
    - 改善并且优化网站导航结构
- **注意事项** 对于前端框架比如（Vue，React等）还需要注释服务端渲染（SSR）或者预渲染，因为搜索引擎爬虫可能无法很好的执行JavaScript代码。

