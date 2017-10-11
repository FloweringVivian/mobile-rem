# mobile-rem
移动端利用js根据屏幕宽度动态改变html的font-size，结合rem实现自适应

```javascript
<script>       
(function (doc, win) {   
    var docEl = doc.documentElement,   
    resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',   
    recalc = function () {   
	var clientWidth = docEl.clientWidth;   
	if (!clientWidth) return;   
	docEl.style.fontSize = 20 * (clientWidth / 320) + 'px';   
    };   
    if (!doc.addEventListener) return;   
    win.addEventListener(resizeEvt, recalc, false);   
    doc.addEventListener('DOMContentLoaded', recalc, false);   
})(document, window);   
</script>
```

加入这么一段js，就可以根据屏幕的宽度动态改变font-size

根据这一句 docEl.style.fontSize = 20 * (clientWidth / 320) + 'px';  可知

iphone4和iphone5宽度是320px，那么font-size就是20px, 如果设置1rem就是20px

iphone6宽度是375px，那么font-size就是23.4375px,如果设置1rem就是23.4375px

这样就可以实现高度的还原设计图，假如设计图是640px的尺寸，一个div的高度是40px，那么我们在写的时候按照最小尺寸的手机型号来写，比如iphone4和iphone5是320px,是设计图宽度的一半，那么我们应该设置height:1rem;这样，div在320px的屏幕上显示出的高度是20px，在640px的屏幕上显示出的高度是40px，因此就做到了还原设计图。

demo效果请查看rem.html
