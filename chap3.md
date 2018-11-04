### width:auto     包裹性的体现

需求：某模块内文字内容是动态的，文字少时居中显示，文字超过一行时居左显示。

```html
<div class="box">
    <p class="content">文字文字</p>
</div>
```

```css
.box{
  width:240px;
  text-align:center;   
}
.content{
  display:inline-block;		!!!很重要
  text-align:left;
}
```

### background-clip

> 规定背景的绘制区域

### background-origin

> background-origin 属性规定 background-position 属性相对于什么位置来定位

#### 以上两个属性的值均为padding-box|border-box|content-box



### offsetWidth=padding+border+width

offsetWidth 仅为可读值，不可更改，返回值为整数，width返回值为带单位的字符串







## CSS流体布局下的宽度分离原则

**分离**----width独占一层标签，padding、border、margin利用流动性在内部自适应呈现

```css
.father{
    width:180px;
}
.son{
    margin:0 20px;
    padding:20px;
    border:1px solid;
}
```



尝试

```css
input,textarea,img,video,object{
    box-sizing:border-box;
}
```



### 实现height: 100%

1. 设定显示的高度值

   ```css
   html,body{
       height: 100%;
   }
   ```

2. 使用绝对定位

   ```css
   div{
       height: 100%;
       position: absolute;
   }
   ```

   **注意**: 绝对定位元素的百分比计算和非绝对定位的百分比计算是有区别的。绝对定位的宽高百分比计算是相对于padding box的，但非绝对定位则是相对于content box的。



### max-width/min-width 和 max-height/min-height 的初始值

1. max-* 的初始值为none
2. min-* 的初始值为auto 



## 实现任意高度元素的展开收起

1. jQuery的slideUp()/slideDown()       (不支持移动端)

2.  

   ```css
   .element{
       max-height: 0;
       overflow: hidden;
       transition: height .25s;
   }
   .element.active{
       max-height:666px;		/* 一个足够大的最大高度值 */
   }
   ```

   **注意**: 如果max-height 太大，在收起时可能会有“效果延迟”的问题。比如说，实际高度为100px,最大高度为1000px ,当max-height从1000到100这段时间内是没有视觉效果的，所以max-height应该使用足够安全的最小值。