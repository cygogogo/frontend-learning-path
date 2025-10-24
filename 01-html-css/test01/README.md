## 1.基本结构
使用快捷键 `!` + `Enter` 可以快速生成HTML基本骨架。

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>页面标题</title>
</head>
<body>
    <!-- 页面内容 -->
</body>
</html>
```

### 说明
- `<!DOCTYPE html>`：文档类型声明
- `<html lang="zh-CN">`：设置中文语言
- `<meta charset="UTF-8">`：设置字符编码

## 2.常用标签
### h1-h6 
用来定义标题，其中`h1`通常只用一次，作为页面主标题。
```html
<h1>一级标题</h1>
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>
```
### p标签
用来定义文本段落，浏览器会自动为`<p>`标签添加上下边距，使其内容更具有可读性。
```html
<p>这是一个段落</p>
<p>这是另一个段落，与上面有自动间距</p>
```
### br标签
单标签，不需要闭合，用来强制换行。
```html
第一行<br>
第二行
```
### hr标签
单标签，不需要闭合，用来创建水平分割线，用于内容分隔。
```html
<hr>
```
### 注释生成
注释快捷键`ctrl`+`/`
```html
<!-- 这是注释，不会在页面显示 -->
<!-- 多行注释
     也可以这样写 -->
```
### 文本格式化标签
```html
<strong>加粗文字</strong>
<b>加粗文字</b>
<em>强调文字</em>
<i>斜体文字</i>
<u>下划线文字</u>
<ins>ins下划线</ins>
<del>删除线文字</del>
<mark>高亮文字</mark>
```
### 超链接
```html
<a href="https://www.example.com" target="_blank">访问示例网站</a>
<a href="#section1">跳转到章节一</a>
<a href="#">空链接</a>
```
- `href`：跳转目标链接
- `#`：空链接或页面锚点
- `target="_blank"`：新窗口打开，不添加默认原窗口打开

## 3.多媒体标签
### 图像
```html
<img src="images/photo.jpg" alt="图片描述" title="图片标题" width="300">
```
- `src`：图像路径（相对路径或绝对路径）
- `alt`：替代文本，图片无法显示时展示，对SEO和无障碍访问很重要
- `title`：提示文本，鼠标悬停时显示
- `width`：设置宽高，当只设置一个时，浏览器会等比例缩放
### 音频
```html
<audio src="audio/music.mp3" controls loop></audio>
```
- `src`：音频路径（相对路径或绝对路径）
- `controls`：显示播放控制面板
- `loop`：循环播放
- `autoplay`：自动播放，为了用户体验，一般不设置
- 支持格式：MP3、WAV、OGG
### 视频
```html
<video src="videos/movie.mp4" controls loop muted width="600"></video>
```
- `src`：视频路径（相对路径或绝对路径）
- `controls`：显示播放控制面板
- `loop`：循环播放
- `muted`：静音播放
- `autoplay`：自动播放，一般搭配`muted`使用
- 支持格式：MP4、WebM、OGG

