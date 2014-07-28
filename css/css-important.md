'!important'浏览器兼容
========================

IE7以上对`!important`是支持的,但IE6对!important只支持单个的类，比如：

```css
.className{color:#ffff00!important}
.className{color:green;}
```

但有多个类是不支持的:

```css
.className{color:#ffff00; color:green}

```