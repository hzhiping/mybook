# 介绍

GitBook 支持相关的插件进行编辑，所以这里我们介绍一下 GitBook 的插件，看看如何使用这些插件，进行页面的设计，使其更加美观。

在 GitBook 中可以在书籍的配置文件 book.json 中来进行插件的相关配置。比如有很多好用的插件，可以很好的拓展书籍的外观，可用性或者其他方便的使用，所以接下来就一起来看看 GitBook 中插件的使用吧。

首先，在和 README.md 和 SUMMARY.md 的同级目录下查看是否有 book.json，如果没有的话，创建一个 book.json，book.json 的大概目录层级如下所示：

```json
{
  "title": "学习笔记",
  "author": "黄志平",
  "plugins": [
    "livereload",
    "anchor-navigation-ex",
    "theme-default",
    "search",
    "chapter-fold",
    "code",
    "splitter",
    "-lunr",
    "-search",
    "search-pro",
    "custom-favicon",
    "pageview-count",
    "tbfed-pagefooter",
    "popup",
    "-sharing",
    "sharing-plus",
    "prism",
    "-highlight"
  ],
  "pluginsConfig": {
    "search": {
      "maxSearchResults": 10
    },
    "hide-element": {
      "elements": [
        ".gitbook-link"
      ]
    },
    "favicon": "icon/favicon.ico",
    "tbfed-pagefooter": {
      "copyright": "Copyright &copy hzhiping.github.io 2019",
      "modify_label": "文章最后修订时间：",
      "modify_format": "YYYY-MM-DD HH:mm:ss"
    },
    "sharing": {
      "douban": true,
      "facebook": true,
      "google": true,
      "pocket": true,
      "qq": true,
      "qzone": true,
      "twitter": true,
      "weibo": true,
      "all": [
        "douban",
        "facebook",
        "google",
        "instapaper",
        "linkedin",
        "twitter",
        "weibo",
        "messenger",
        "qq",
        "qzone",
        "viber",
        "whatsapp"
      ]
    },
    "prism": {
      "css": [
        "prismjs/themes/prism-solarizedlight.css"
      ],
      "lang": {
        "flow": "typescript"
      },
      "ignore": [
        "mermaid",
        "eval-js"
      ]
    }
  },
  "structure": {
    "readme": "README.md"
  }
}
```

# 默认插件

在 GitBook 中自带了 5 个默认的插件：

- highlight：语法高亮插件，代码高亮功能
- search：搜索插件，不支持中文搜索
- sharing：分享插件，右上角分享功能
- livereload：热加载插件，为 GitBook 编辑进行实时重新预览加载

## 禁用插件

如果需要去除或者禁用 GitBook 中的某个插件，可以在插件名称前面添加“-”即可：

```
"plugins": [
    "-search",
    "-highlight",
    "-sharing",
    "-font-settings",
    "-livereload",
    ...
]
```

## 添加插件

如果需要添加一些第三方的自定义插件，可以在 plugins 中添加需要的插件名称列表：

```
"plugins": [
    "-search",
    "advanced-emoji",
    "search-pro",
    "github",
    "splitter",
    "anchor-navigation-ex",
    "chapter-fold",
    "expandable-chapters-small",
    "code",
    "alerts",
    "insert-logo",
    "flexible-alerts",
    ...
]
```

## 插件属性的配置

配置插件的属性在书籍配置文件中的 pluginsConfig 中进行相关插件的属性配置。

例如要配置 insert-logo 插件的相关属性：

```
"pluginsConfig": {
   "insert-logo": {
       "url": "jim-logo.png",
       "style": "background: none; max-height: 100px; min-height: 30px"
   }
}
```

# 实用的插件

实用的插件介绍如下：

```json
{
  "title": "学习笔记",
  "author": "黄志平",
  "plugins": [
    // 热部署，目前不知道为什么，这个插件不能实现热部署，没找到办法，知道可告知一下。
    "livereload",
    // 插件会在右上角添加一个 github 的图标，可以通过插件属性配置链接，点击后可以进入自定义的链接页面
    "github",
    // 可以在 GitBook 使用 emoji 表情
    "advanced-emoji",
    "image-captions",
    // 悬浮目录和回到顶部
    "anchor-navigation-ex",
    // 折叠侧边栏
    "expandable-chapters-small",
    // 默认主题
    "theme-default",
    "search",
    // 章节折叠插件
    "chapter-fold",
    "code",
    "splitter",
    "-lunr",
    "-search",
    "search-pro",
    "custom-favicon",
    "pageview-count",
    // 页脚和版权
    "tbfed-pagefooter",
    "popup",
    "-sharing",
    "sharing-plus",
    // 代码高亮主题
    "prism",
    // 禁用默认主题
    "-highlight"
  ],
  "pluginsConfig": {
    "search": {
      "maxSearchResults": 10
    },
    "hide-element": {
      "elements": [
        ".gitbook-link"
      ]
    },
    "favicon": "icon/favicon.ico",
    "tbfed-pagefooter": {
      "copyright": "Copyright &copy hzhiping.github.io 2019",
      "modify_label": "文章最后修订时间：",
      "modify_format": "YYYY-MM-DD HH:mm:ss"
    },
    "sharing": {
      "douban": true,
      "facebook": true,
      "google": true,
      "pocket": true,
      "qq": true,
      "qzone": true,
      "twitter": true,
      "weibo": true,
      "all": [
        "douban",
        "facebook",
        "google",
        "instapaper",
        "linkedin",
        "twitter",
        "weibo",
        "messenger",
        "qq",
        "qzone",
        "viber",
        "whatsapp"
      ]
    },
    "prism": {
      "css": [
        "prismjs/themes/prism-solarizedlight.css"
      ],
      "lang": {
        "flow": "typescript"
      },
      "ignore": [
        "mermaid",
        "eval-js"
      ]
    },
    "github": {
      "url": "https://github.com/hzhiping"
    }
  },
  "structure": {
    "readme": "README.md"
  }
}
```