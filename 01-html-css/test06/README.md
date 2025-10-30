# 浮动和flex

## 1.浮动
使元素脱离文档流，向指定方向浮动，直到碰到父元素边缘或其他浮动元素，常用于实现多元素横向排列布局。
```html
    float:方向;/*left、right*/
```
多个浮动元素默认沿顶部对齐。  
浮动元素可像行内块一样在同一行排列，且能设置宽高（区别于普通行内元素）。  
浮动元素脱离标准文档流，不占据原位置，后续元素会向上填充其空间，可能导致父元素高度塌陷，需额外处理。  
若父容器宽度不足以容纳所有浮动元素，最后一个元素会 “掉下来”，即换行显示；需确保浮动元素总宽度（含间距）≤ 父容器宽度。  

## 2.清除浮动
当父元素未设置固定高度时，内部浮动元素脱标会导致父元素无法被内容撑开，高度为 0，影响后续元素布局。
### 额外标签法  
在父元素内容的最后添加一个块级元素，设置`clear:both`
```html
        .clearfix{
            clear:both;
        }
```
### 单伪元素法
先给父元素添加`class="clearfix"`，利用`::after`伪元素在父元素尾部添加虚拟块级元素，替代额外标签，避免冗余 HTML。
```html
    .clearfix::after{
        content:"";
        display:block;
        clear:both;
    } 
```
### 双伪元素法
在单伪元素基础上增加`::before`，同时解决浮动元素与父元素顶部的 margin 坍塌问题。
```html
            .clearfix::before,
            .clearfix::after{
                content:"";
                display:table;/* 触发 BFC，隔离margin */
            } 
            .clearfix::after{
                clear:both;/* 清除浮动 */
            }
```

## 3.flex布局
通过给父元素设置`display: flex`开启弹性布局，父元素称为 “弹性容器”，子元素称为 “弹性项目”。  
项目默认沿主轴水平方向进行排列，摆脱文档流限制，无需浮动即可横向排列。  
### justify-content 主轴对齐
控制项目在主轴（默认水平）的排列方式。
```html
    justify-content: 属性值;
```
`flex-start`：项目从主轴起点（左）排列（默认）  
`flex-end`：项目从主轴终点（右）排列  
`center`：项目沿主轴居中排列  
`space-between`：项目间距相等，首尾贴容器两端  
`space-around`：项目间距是首尾到容器间距的 2 倍  
`space-evenly`：所有间距（含首尾）完全相等  

###  align-items 侧轴对齐
控制项目在侧轴（默认垂直）的对齐方式，需容器有固定高度才明显。
```html
    align-items: 属性值;
```
`stretch`：项目拉伸至与容器等高，需项目无固定高度  
`center`：项目沿侧轴居中对齐  
`flex-star`t：项目从侧轴起点（上）排列  
`flex-end`：项目从侧轴终点（下）排列  

### flex-direction 主轴方向
修改主轴的方向，影响 justify-content 和 align-items 的控制方向。
```html
    flex-direction: 属性值;
```
`row`：主轴水平（左→右，默认）  
`column`：主轴垂直（上→下）  
`row-reverse`：主轴水平（右→左）  
`column-reverse`：主轴垂直（下→上）  

### flex-wrap 项目换行
控制项目超出容器时是否换行，避免项目被压缩。
```html
    flex-wrap: 属性值;
```
`wrap`：自动换行（从上到下）  
`nowrap`：不换行，压缩项目尺寸（默认）  

### align-content 多行侧轴对齐
仅当项目换行时生效，控制多行项目的整体侧轴对齐。
```html
    align-content: 属性值;
```
常用属性值与`justify-content`的一致。

### align-self 单个项目侧轴对齐
单独设置某个项目的侧轴对齐，覆盖容器的`align-items`。  
常用属性值与`align-items`一致。  

### flex 项目伸缩比
控制项目在主轴方向的伸缩比例，分配容器剩余空间。  
常用属性值：正整数（代表权重，总和为总份数，项目占比 = 自身数值 / 总份数）  
`flex: 1`：占剩余空间的 1 份  
`flex: 2`：占剩余空间的 2 份  
