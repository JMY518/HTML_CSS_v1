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
- `<html>`标签同时支持所有**全局属性**如`class`,`id`,`style`。

⚠️ `<!DOCTYPE html>`为**文档类型声明**（Document Type Declaration），并非`<html>`标签，用于告诉浏览器当前文档使用的是HTML5标准。详情前往[`<!DOCTYPE html>`](#)

### `<head>` 元数据
- `<head>`标签包含这个HTML文档的**元数据**（metadata），元数据不会直接显示为页面内容，而是会影响浏览器的**渲染**，**抓取**，以及外部资源的**加载**。
- **位置：** 必须位于[`<html>`](#html根标签)标签内，并且在[`<body>`](#body-内容标签)标签之前。
```html
    
```

### `<body>` 内容标签
占位----
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

