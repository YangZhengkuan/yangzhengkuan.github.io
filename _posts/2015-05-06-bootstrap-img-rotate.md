---
layout: post
title: 相册显示-图片旋转
tags: Bootstrap html5 css
---

使用html5中data-*自定义属性为img标签添加角度属性，并使用-webkit-transform样式进行图片旋转，实现相册中常见的图片旋转功能。

[演示地址](https://yangzhengkuan.github.io/html/2015-05-06-bootstrap-img-rotate.html)

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <meta http-equiv="Content-Type" content="text/html">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="Keywords" content="关键词">
    <meta name="description" content="沙漠胡杨 2015-5-6">
    <title>相册-图片旋转</title>
    <style type="text/css">
        * {
            font-family: "微软雅黑";
        }
    </style>
    <link href="https://libs.baidu.com/bootstrap/3.0.3/css/bootstrap.min.css" rel="stylesheet">
</head>

<body>

<nav class="navbar navbar-default navbar-static-top" role="navigation">
    <div class="navbar-header">
        <a class="navbar-brand" href="#">相册-图片旋转</a>
    </div>
</nav>

<div class="container">
    <div class="jumbotron">
        <img class="img-circle" src="../assets/img/logo.jpg" alt="mylogo" width="100" height="100">
        <span class="h2">相册显示-图片旋转</span>

        <div class="row" style="margin-top:30px;">
            <div class="item col-sm-6 col-md-3">
                <a class="thumbnail">
                    <img src="../assets/img/logo.jpg" data-deg="0" alt="" width="200" height="200">
                </a>
                <a class="btn btn-primary btn-lg" role="button" onclick="transform(this);">旋转</a>
            </div>
            <div class="item col-sm-6 col-md-3">
                <a class="thumbnail">
                    <img src="../assets/img/logo.jpg" data-deg="0" alt="" width="200" height="200">
                </a>
                <a class="btn btn-primary btn-lg" role="button" onclick="transform(this);">旋转</a>
            </div>
            <div class="item col-sm-6 col-md-3">
                <a class="thumbnail">
                    <img src="../assets/img/logo.jpg" data-deg="0" alt="" width="200" height="200">
                </a>
                <a class="btn btn-primary btn-lg" role="button" onclick="transform(this);">旋转</a>
            </div>
            <div class="item col-sm-6 col-md-3">
                <a class="thumbnail">
                    <img src="../assets/img/logo.jpg" data-deg="0" alt="" width="200" height="200">
                </a>
                <a class="btn btn-primary btn-lg" role="button" onclick="transform(this);">旋转</a>
            </div>
        </div>
    </div>
</div>
<script src="https://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
<script src="https://libs.baidu.com/bootstrap/3.0.3/js/bootstrap.min.js"></script>
<script type="text/javascript">

    //旋转
    function transform(obj) {
        var img = $(obj).parents(".item").find("img");
        var deg = img.data("deg");
        deg = deg + 90;
        if (deg >= 360) {
            deg = 0;
        }
        img.data("deg", deg);
        img.css("-webkit-transform", "rotate(" + deg + "deg)");
    }
</script>

</body>
</html>
```

