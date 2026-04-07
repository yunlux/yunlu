---
{"dg-publish":true,"permalink":"/05 - 计算机，AI/PKM/【Obsidian 外观】给 Properties 加上书籍封面/","title":"【Obsidian 外观】给 Properties 加上书籍封面","tags":["网页剪切"],"created":"2025-04-08T04:43:01.199+08:00","updated":"2025-04-08T04:59:07.935+08:00","dg-note-properties":{"title":"【Obsidian 外观】给 Properties 加上书籍封面","source":"https://www.bilibili.com/opus/836558444158779409?spm_id_from=333.1387.0.0","author":["[[哔哩哔哩]]"],"published":null,"created":"2025-04-08","description":null,"tags":["网页剪切"]}}
---

- [创作中心](https://member.bilibili.com/platform/home)

Obsidian官方

【Obsidian 外观】给 Properties 加上书籍封面 Obsidian官方编辑于 2023年09月02日 16:36收录于文集 Obsidian 分享 · 1篇

来自 Discord 社区用户 @reaty 的样式分享：

```css
.book .cm-scroller {
padding-left: 10% !important;
padding-right: 10% !important;
}

.book .cm-sizer,
.book .markdown-preview-sizer {
    margin-left: 0px !important;
    margin-right: 0px !important;
}

.book .inline-title {
display: none;
}

.book img[alt=&quot;cover&quot;] {
    width: 300px;
    height: 500px;
    object-fit: cover;
   }

.book.is-live-preview .metadata-container,
.book.markdown-preview-view .metadata-container {
    position: absolute;
    display: block;
    width: calc(80% - 330px);
    left: calc(10% + 330px);
    max-height: 500px;
    overflow-y: scroll
}
```

使用效果

![e40167649e003da51d5499cde5c18c8b_3af2b6711c849449655853536fce6dd6d02cca8b.jpg@1192w.webp](/img/user/09%20-%20%E7%BD%91%E9%A1%B5%E5%89%AA%E5%88%87/files/e40167649e003da51d5499cde5c18c8b_3af2b6711c849449655853536fce6dd6d02cca8b.jpg@1192w.webp)


使用方式

1、在桌面新建一个 book.txt，打开编辑且将上述代码内容复制后插入其中；

2、修改该文件的后缀名为 css；

3、将该文件移入你的库文件的.obsidian/snippets 文件中（如果你的.obsidian 文件夹中没有 snippets 文件夹，那么你需要自己创建一个 snippets 文件夹）；

4、在你的设置中找到外观设置，滚动到底部，点击刷新按钮，就能发现样式文件已经出现在可选项中，点击以开启它；

5、在你的任意 Markdown 文件的顶部加入 cssClasses 属性，而后输入 book 作为标记当前文件会采用该个 css；

6、在你编辑的当前文件中首行（最好）插入一个图片，并且将其别名设置为 cover；例如!\[\[图片.png|cover\]\] 或者!\[cover\](图片.png)

7、搞定！

