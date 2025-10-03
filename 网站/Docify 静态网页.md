# index.html

```js
<!DOCTYPE html>
<html lang="en">
<!--目前还存在问题：下一页导航，有些显示问题-->

<head>
    <!-- 页面头部信息 -->
    <meta charset="UTF-8">
    <title>XQ_RearchDocument</title>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <meta name="description" content="Description">
    <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!-- 设置浏览器图标 -->
    <link rel="icon" href="/favicon.ico" type="image/x-icon" />
    <link rel="shortcut icon" href="/favicon.ico" type="image/x-icon" />
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/prismjs@1.29.0/plugins/line-numbers/prism-line-numbers.min.css">
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/prismjs@1.29.0/themes/prism.css">
    
    <!-- 默认主题 -->
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/lib/themes/vue.css">
    <!--主题可选-->
<!--
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/buble.css">
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dark.css">
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/pure.css">
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dolphin.css"> -->

    <style type="text/css">	
        .markdown-section pre[data-lang] {
            overflow: auto !important;
        }
        
        .markdown-section pre[data-lang] code {
            overflow: visible;
        }
    
        .line-numbers .line-numbers-rows {
            border-right : 0px solid white;
            /* Fix paddings to align with code.*/
            padding: 5px; /* Same as code block */
        }
        
        .markdown-section pre > code {
            padding: 5px;
        }
      </style>

<style>
.code-container {
    display: flex; /* 使用 flex 布局 */
    background: rgba(240, 240, 240, 0.8); /* 设置背景色 */
    border-radius: 5px; /* 圆角 */
    margin-bottom: 1em; /* 底部间距 */
    padding: 10px; /* 内边距 */
}

.line-numbers {
    width: 40px; /* 行号区域的宽度 */
    padding: 0; /* 行号内边距 */
    user-select: auto; /* 禁用选择行号 */
    text-align: left; /* 右对齐行号 */
    color: #888; /* 行号颜色 */
    background: transparent; /* 背景透明 */
    margin-right: 10px; /* 右边距以分隔行号和代码 */
}

.line-number {
    display: block; /* 行号独占一行 */
}

pre {
    margin: 0; /* 消除默认的上下边距 */
    overflow: auto; /* 确保代码可滚动 */
    flex-grow: 1; /* 让代码区占据剩余空间 */
    padding: 0 10px; /* 代码区内边距 */
    background: #fff; /* 代码块背景色 */
    border: 1px solid #e0e0e0; /* 代码块边框 */
    border-radius: 5px; /* 圆角 */
    font-family: monospace; /* 字体 */
    line-height: 1.5; /* 行高 */
    color: #333; /* 代码字体颜色 */
}

    </style>
    

</head>

<body>
    <!-- 定义加载时候的动作 -->
    <div id="app">Loading...</div>
    <script>
        window.$docsify = {
            // 项目名称
            name: 'DocsifyMaster',
            // 仓库地址，点击右上角的Github章鱼猫头像会跳转到此地址
            repo: 'https://github.com/ruanjianshi?tab=repositories',
            // 侧边栏支持，默认加载的是项目根目录下的_sidebar.md文件
            loadSidebar: true,
            autoHeader: true,
            // 导航栏支持，默认加载的是项目根目录下的_navbar.md文件
            loadNavbar: true,
            // 封面支持，默认加载的是项目根目录下的_coverpage.md文件
            coverpage: true,
            // 最大支持渲染的标题层级
            maxLevel: 5,
            // 自定义侧边栏后默认不会再生成目录，设置生成目录的最大层级（建议配置为2-4）
            subMaxLevel: 4,
            // 小屏设备下合并导航栏到侧边栏
            mergeNavbar: true,
            //切换页面后是否自动跳转到页面顶部
            auto2top:true,
            //文档加载的根路径，可以是二级路径或者是其他域名的路径
            //basePath:'/',
            /* // 直接渲染其他域名的文档
            basePath: 'https://docsify.js.org/',
            // 甚至直接渲染其他仓库
            basePath:'https://raw.githubusercontent.com/ryanmcdermott/clean-code-javascript/master/', */
            // 启用相对路径
            relativePath: true,
            //加载侧边栏中出现的网页图标
            logo: '_media/LogosBun.svg',
            //替换主题色
            //themeColor:'#3F51B5',
            //执行文档里的script标签
            executeScript: true,
            //禁用 emoji 解析
            noEmoji:false,
            //文档变更日期
            formatUpdated: '{MM}/{DD} {HH}:{mm}',
            formatUpdated: function(time) {
              // ...

              return time;
            },
            //外部链接的打开方式
            externalLinkTarget: '_blank', // default: '_blank'
            //右上角链接的打开方式
            cornerExternalLinkTarget: '_blank', // default: '_blank'
            //防止新打开的页面能够控制我们的页面
            externalLinkRel: 'noopener', // default: 'noopener'
            //不希望 docsify 处理我们的链接
            //noCompileLinks: ['/foo', '/bar/.*'],
            //滚动锚点，可以距离页面顶部有一定的空间
            topMargin: 90, // default: 0
            //创建并注册全局 Vue组件 
            vueComponents: {
             'button-counter': {
                 template: `
                     <button @click="count += 1">
                        You clicked me {{ count }} times
                     </button>
                    `,
                data() {
                     return {
                         count: 0,
                         };
                    },
                 },
            },
            vueGlobalOptions: {
             data() {
                return {
                        count: 0,
                    };
                },
            },
            vueMounts: {
             '#counter': {
                data() {
                    return {
                      count: 0,
                          };
                      },
                 },
            },
            //分页导航设置
            pagination: {
                 previousText: '上一章节',
                 nextText: {
                 '/en/': 'NEXT',
                 '/': '下一章节',
                },
                crossChapter: true,
                crossChapterText: true,
            },
            //字数统计配置
            count:{
                countable:true,
                fontsize:'0.9em',
                color:'rgb(90,90,90)',
                language:'chinese'
            },
            //标签TAB
            tabs: {
                persist: true, // default
                sync: true, // default
                theme: 'classic', // default
                tabComments: true, // default
                tabHeadings: true // default
            },
            /*搜索相关设置*/
            search: {
                maxAge: 86400000,// 过期时间，单位毫秒，默认一天
                paths: 'auto',// 注意：仅适用于 paths: 'auto' 模式
                placeholder: '搜索',              
                // 支持本地化
                placeholder: {
                    '/zh-cn/': '搜索',
                    '/': 'Type to search'
                },
                noData: '找不到结果',
                depth: 4,
                hideOtherSidebarContent: false,
                namespace: 'DocsifyMaster',
            },
            //GITHUB上编辑
            plugins: [
                function(hook, vm) {
                hook.beforeEach(function(html) {
                    var url =
                    'https://github.com/ruanjianshi/XQ_BLOG/blob/master/' +
                    vm.route.file;
                    var editHtml = '[📝 EDIT DOCUMENT](' + url + ')\n';

                    return (
                    editHtml +
                    html +
                    '\n----\n' +
                    'Last modified {docsify-updated} ' +
                    editHtml
                    );
                });
                }
            ],
             // 页面右侧toc
            toc: {
            tocMaxLevel: 2,
            target: "h2, h3, h4, h5, h6",
            },
            //代码行显示
            markdown: {
        renderer: {
            code: function(code, lang) {
                return '<pre data-lang="' + lang + '"><code class="line-numbers language-' + lang + '">' + code + '</code></pre>';
            }
        }
    },
            plugins: [
                function (hook, vm) {
                    hook.doneEach(function (html) {                
                        Prism.highlightAll();
                    })
                }
            ], 
            //routerMode: 'history',
                
         /*    markdown: {
                smartypants: true,
                renderer: {
                link: function() {
                    // ...
                }
                }
            } */
           // disqus: 'shortname'

         /*   markdown: function(marked, renderer) {
                // ...

                return marked
            } */
       
    }
    </script> 
    <script src="highlight-line.js"></script>
    <script src="read-num.js"></script>
    <!--加密文本 CRYPOTOJS库-->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/3.1.9-1/crypto-js.js"></script> 
    
    <script src="document_encryption.js"></script>
    <!-- docsify-tabs (latest v1.x.x) -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-tabs@1"></script>

<!-- 添加预览滚动效果，但是会导致无法跳转
    <style type="text/css">
        .content {
         overflow: auto;
    }
    </style>
-->
    <!--代码行显示存在问题，后续有时间修改-->
    <script src="//cdn.jsdelivr.net/npm/prismjs@1.29.0/plugins/line-numbers/prism-line-numbers.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1.29.0/components/prism-core.min.js"></script>
    <!-- 侧边栏目录折叠 -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>

    <!-- 页面右侧 TOC -->
    <script src="https://cdn.jsdelivr.net/npm/docsify-plugin-toc@1.1.0/dist/docsify-plugin-toc.min.js"></script>
    <!--添加Disqus评论系统-->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/disqus.min.js"></script>
    <!--加载vue-->
    <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
    <!-- docsify的js依赖 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
    <!-- emoji表情支持 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
    <!-- 图片放大缩小支持 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
    <!-- 搜索功能支持 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
    <!--在所有的代码块上添加一个简单的Click to copy按钮来允许用户从你的文档中轻易地复制代码-->
    <script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
    <!--分页导航-->
    <script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>
    <!--字数统计-->
    <script src="//unpkg.com/docsify-count/dist/countable.js"></script>
    <!--代码高亮，需要在所添加代码第一行添加语言声明-->
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-php.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-c.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-cpp.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-cpp.min.js"></script>

</body>

<!--定义TAB标签样式-->
<!-- <style>
    :root {
        /* Tab blocks */
        --docsifytabs-border-color: #ededed;
        --docsifytabs-border-px: 1px;
        --docsifytabs-border-radius-px: ;
        --docsifytabs-margin: 1.5em 0;
      
        /* Tabs */
        --docsifytabs-tab-background: #f8f8f8;
        --docsifytabs-tab-background--active: var(--docsifytabs-content-background);
        --docsifytabs-tab-color: #999;
        --docsifytabs-tab-color--active: inherit;
        --docsifytabs-tab-highlight-px: 3px;
        --docsifytabs-tab-highlight-color: var(--theme-color, currentColor);
        --docsifytabs-tab-padding: 0.6em 1em;
      
        /* Tab content */
        --docsifytabs-content-background: inherit;
        --docsifytabs-content-padding: 1.5rem;
      }
    </style> -->

<!--评论系统-->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.css">
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/gitalk.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.min.js"></script>
<script>
 const gitalk = new Gitalk({
    id: decodeURI('{{ page.url }}'),
    clientID: 'Ov23lieSfcUy64KUFiKU',
    clientSecret: 'b54a7acbc68bd907eccd1fde147d977ab99bc928',
    repo: 'discuss_gitalk',
    owner: 'ruanjianshi',
    admin: ['ruanjianshi'],
    //title: 'xq',
    distractionFreeMode: false
  })
</script> 

</html>
```

# document_encryption.js

```js
(function () {
    //依赖https://github.com/brix/crypto-js
    if (!window.$docsify) {
        return;
    }

    function parsePwd(content) {
        const urlParams = new URLSearchParams(window.location.search);
        const pwdParam = urlParams.get('pwd');

        // 改进正则表达式以提高效率
        return content.replace(/<pwd\s+(.*?)>([\s\S]*?)<\/pwd>/g, function (match, attributes, pwdContent) {
            const attributesMap = {};
            attributes.replace(/(\w+)=['"](.*?)['"]/g, (match, key, value) => {
                attributesMap[key] = value;
            });

            const { value: password = '', pwd = '', url: urlContent = '' } = attributesMap;
            
            if (pwdParam === password) {
                return pwdContent; // 如果 URL 参数匹配，则显示 <pwd> 标签内容
            } 
            
            if (pwdParam) {
                alert("密码错误,请重新输入");
            }
            
            return `<p style="text-align: center;"><img src="${urlContent}" data-origin="_media/get_password.jpg" alt="无法加载图片..." width="250" height="250"/></p>
                    <p style="text-align: center;"><strong>扫码添加微信获取密码${pwd}</strong></p>
                    <p style="text-align: center;"><input id ="pwd" /> <button onclick="addParamAndRefresh()">确定</button></p>`;
        });
    }

    // Parse <pwd> tags in the page content
    function parseContent(content) {
        return parsePwd(content);
    }

    const afterEachHook = function (hook, vm) {
        hook.beforeEach((html, next) => {
            next(parseContent(html));
        });
    }

    window.$docsify.plugins = [afterEachHook, ...(window.$docsify.plugins || [])];
})();

// 点击按钮时执行的函数
function addParamAndRefresh() {
    const inputElement = document.getElementById('pwd');
    const inputValue = inputElement.value.trim();

    if (!inputValue) {
        alert("输入不能为空，请输入密码");
        return;
    }

    const urlParams = new URLSearchParams(window.location.search);
    urlParams.set('pwd', inputValue);

    // 更新当前页面URL
    const newURL = `${window.location.origin}${window.location.pathname}?${urlParams.toString()}`;
    window.location.href = newURL;
}
```

# highlight-line.js

```js
(function () {
    window.$docsify.plugins.push(function (hook) {
        hook.afterEach(function (html) {
            // 使用 DOMParser 创建一个 DOM 文档
            var parser = new DOMParser();
            var doc = parser.parseFromString(html, 'text/html');

            // 查找所有的代码块
            var codeBlocks = doc.querySelectorAll('pre');

            codeBlocks.forEach(function (block) {
                // 获取代码行
                var code = block.querySelector('code');
                if (!code) return; // 确保存在代码块

                var lines = code.innerHTML.split('\n');
                var lineCount = lines.length;

                // 创建行号的HTML
                var lineNumbers = '<div class="line-numbers">';
                for (let i = 1; i <= lineCount + 1; i++) {
                    lineNumbers += '<span class="line-number">' + i + '</span>';
                }
                lineNumbers += '</div>';

                // 使用原始的 code HTML，确保 Prims.js 的类保留
                var combinedHTML = `<div class="code-container">${lineNumbers}<pre>${code.outerHTML}</pre></div>`;
                block.innerHTML = combinedHTML; // 替换原代码块内容
            });

            // 返回处理后的 HTML
            return doc.body.innerHTML;
        });
    });
})();
```

# read-num.js

```js
(function () {
    window.$docsify.plugins.push(function (hook) {
        hook.afterEach(function (html) {
            // 使用 DOMParser 创建一个 DOM 文档
            var parser = new DOMParser();
            var doc = parser.parseFromString(html, 'text/html');

            // 查找所有的代码块
            var codeBlocks = doc.querySelectorAll('pre');

            codeBlocks.forEach(function (block) {
                // 获取代码行
                var code = block.querySelector('code');
                if (!code) return; // 确保存在代码块

                var lines = code.innerHTML.split('\n');
                var lineCount = lines.length;

                // 创建行号的HTML
                var lineNumbers = '<div class="line-numbers">';
                for (let i = 1; i <= lineCount + 1; i++) {
                    lineNumbers += '<span class="line-number">' + i + '</span>';
                }
                lineNumbers += '</div>';

                // 使用原始的 code HTML，确保 Prims.js 的类保留
                var combinedHTML = `<div class="code-container">${lineNumbers}<pre>${code.outerHTML}</pre></div>`;
                block.innerHTML = combinedHTML; // 替换原代码块内容
            });

            // 返回处理后的 HTML
            return doc.body.innerHTML;
        });
    });
})();
```

# Markdown

- README.md :是项目的主要文档，通常包含项目的基本信息、安装指南、使用方法等。它是 GitHub 等代码托管平台上显示的默认页面。
- _navbar.md:用于自定义网站导航栏的内容，通常是一个配置文件。在一些文档生成工具中，它指定了顶部导航栏的菜单项和链接。
- _coverpage.md:是用于自定义网站封面页的内容。这个文件通常是用来定义网站的欢迎页面或首页的外观，比如站点的标题、描述、logo 和其他封面元素。
- _sidebar.md:用于定义网站的侧边栏菜单。通过该文件，可以控制文档结构的层次，设置每个页面的链接，使访问者可以方便地浏览文档。

在项目中，文件如 `README.md`、`_navbar.md`、`_coverpage.md` 和 `_sidebar.md` 通常用于静态网站生成器（如 **Docusaurus**、**VuePress** 或 **MkDocs**）或文档管理系统中，作为不同的配置文件，用于构建网站的结构、内容和样式。这里，我将解释每个文件的用途并提供基本示例。

## **`README.md`**:

`README.md` 是项目的主要文档，通常包含项目的基本信息、安装指南、使用方法等。它是 GitHub 等代码托管平台上显示的默认页面。

#### 示例内容：

```
# 项目名称

项目描述，例如：这是一个用于管理文档的静态网站生成器。

## 安装

```bash
npm install
```

## _navbar.md

- 自动生成目录
- 自定义主题
- 支持 Markdown 格式

```
### 2. **`_navbar.md`**:
`_navbar.md` 用于自定义网站导航栏的内容，通常是一个配置文件。在一些文档生成工具中，它指定了顶部导航栏的菜单项和链接。

#### 示例内容：
```markdown
# 顶部导航栏

- [首页](./index.md)
- [文档](./docs.md)
- [API 参考](./api.md)
- [联系我们](./contact.md)
```

在某些工具（如 **MkDocs**）中，`_navbar.md` 可能并不是一个标准的配置文件，导航栏的内容可能直接写在配置文件中，例如 `mkdocs.yml`。

## **`_coverpage.md`**:

`_coverpage.md` 是用于自定义网站封面页的内容。这个文件通常是用来定义网站的欢迎页面或首页的外观，比如站点的标题、描述、logo 和其他封面元素。

### 示例内容：

```
# 欢迎来到我的文档站点

这是一个示例封面页，用于展示站点的基本信息和目的。

## 站点简介

- **主题**：简洁现代
- **功能**：自动目录生成、API 文档支持

[开始阅读](./docs/getting-started.md)
```

## **`_sidebar.md`**:

`_sidebar.md` 用于定义网站的侧边栏菜单。通过该文件，可以控制文档结构的层次，设置每个页面的链接，使访问者可以方便地浏览文档。

### 示例内容：

```
# 侧边栏

- [首页](./index.md)
- [文档](./docs.md)
  - [入门指南](./docs/getting-started.md)
  - [进阶教程](./docs/advanced.md)
- [API 参考](./api.md)
- [常见问题](./faq.md)
```

在一些静态网站生成器中，`_sidebar.md` 是一个用于构建侧边栏导航的配置文件。比如在 **MkDocs** 中，可以直接通过 `mkdocs.yml` 来配置侧边栏内容。

------

## 综合示例：如何组织这些文件

假设你正在构建一个文档站点，以下是一个简单的文件结构和内容：

```
/docs
  ├── index.md
  ├── getting-started.md
  ├── advanced.md
  └── api.md
/_navbar.md
/_coverpage.md
/_sidebar.md
README.md
```

#### `_navbar.md`：

```
# 顶部导航栏

- [首页](./index.md)
- [文档](./docs.md)
- [API 文档](./api.md)
- [支持](./contact.md)
```

#### `_coverpage.md`：

```
# 欢迎使用我的文档站点

探索我们的文档，学习如何使用我们的工具。

[立即开始](./docs/getting-started.md)
```

#### `_sidebar.md`：

```
# 侧边栏

- [首页](./index.md)
- [文档](./docs.md)
  - [入门指南](./getting-started.md)
  - [进阶教程](./advanced.md)
- [API 参考](./api.md)
```

#### `README.md`：

```
# 项目名称

这是一个示例项目，演示如何使用 Markdown 文件构建文档站点。

## 功能
- 生成静态网站
- 支持多层级文档结构
- 自动生成导航栏和侧边栏

## 安装

```bash
npm install

---

### 总结：
- **`README.md`**：项目的概述、安装和使用说明。
- **`_navbar.md`**：定义顶部导航栏的内容和链接。
- **`_coverpage.md`**：定制封面页（欢迎页面）。
- **`_sidebar.md`**：定义侧边栏的结构，帮助用户浏览文档。

这些文件的组织和内容可能会根据你使用的静态网站生成器或文档框架的不同而有所不同。一般来说，这些文件都是用来控制文档站点的结构、导航和样式。
```

# 布局效果

![2024-12-26-163738-1024x537](http://qxmapdepot.xiaoq11.cn/picture/2024-12-26-163738-1024x537.png)![2024-12-26-163821-1024x512](http://qxmapdepot.xiaoq11.cn/picture/2024-12-26-163821-1024x512.png)![2024-12-26-163512-1024x501](http://qxmapdepot.xiaoq11.cn/picture/2024-12-26-163512-1024x501.png)