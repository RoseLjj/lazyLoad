# lazyload

## 需要引入jquery

```
 <script src="./js/jquery-1.11.0.js"></script>
 <script src="./js/jquery.lazyload.min.js"></script>

```

## img必须设定宽高,否则无法预加载

```

 <img class="lazy" width="100" height="300" data-original="./img/bmw_m1_hood.jpg">
 <img class="lazy" width="100" height="300" data-original="./img/bmw_m1_side.jpg">

```

## 初始化lazyload

```
<script type="text/javascript" charset="utf-8">
  $(function() {
      $("img.lazy").lazyload({effect: "fadeIn"});
  });
</script>
```

```
$("img.lazy").lazyload({
  placeholder : "img/grey.gif", //用图片提前占位
    // placeholder,值为某一图片路径.此图片用来占据将要加载的图片的位置,待图片加载时,占位图则会隐藏
  effect: "fadeIn", // 载入使用何种效果
    // effect(特效),值有show(直接显示),fadeIn(淡入),slideDown(下拉)等,常用fadeIn
  threshold: 200, // 提前开始加载
    // threshold,值为数字,代表页面高度.如设置为200,表示滚动条在离目标位置还有200的高度时就开始加载图片,可以做到不让用户察觉
  event: 'click',  // 事件触发时才加载
    // event,值有click(点击),mouseover(鼠标划过),sporty(运动的),foobar(…).可以实现鼠标莫过或点击图片才开始加载,后两个值未测试…
  container: $("#container"),  // 对某容器中的图片实现效果
    // container,值为某容器.lazyload默认在拉动浏览器滚动条时生效,这个参数可以让你在拉动某DIV的滚动条时依次加载其中的图片
  failurelimit : 10 // 图片排序混乱时
     // failurelimit,值为数字.lazyload默认在找到第一张不在可见区域里的图片时则不再继续加载,但当HTML容器混乱的时候可能出现可见区域内图片并没加载出来的情况,failurelimit意在加载N张可见区域外的图片,以避免出现这个问题.
});

```


| 属性        | 默认值    |  描述  |  备注  |
| --------   | -----:   | :----: | :----: |
| threshold       | 0      |   临界点    | 可以设置>0的数值，让图片距离屏幕一定像素时提前加载。|
| failure_limit	 | 0 |	当图像不连续时 |	滚动页面的时候, Lazy Load 会循环为加载的图片. 在循环中检测图片是否在可视区域内. 默认情况下在找到第一张不在可见区域的图片时停止循环. 图片被认为是流式分布。特殊布局请设高参数。|
| container	  | window |	触发可滚动的容器 |	默认是浏览器的滚动条，也就是window。可以自定义带滚动条的 DIV 元素。如：$("#container")|
|event |	scroll	| 设置事件来触发加载	| click、mouseover可自定义事件|
|effect |	show |	载入特效 |	fadeIn（淡入效果）|
|skip_invisible	|true |	加载隐藏的图片 |	默认忽略了隐藏图片，可以设置为false加载隐藏图片|
|placeholder |	data:image/png;base64,iVBOR…… |	默认的占位图片 |	可以直接把占位的图片路径赋给img的src|