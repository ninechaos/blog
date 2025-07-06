#### 备案号  网站运行天数

修改文件  `./usr/themes/defult/footer.php`

获取的时间是unix时间戳，*从1970年1月1日（UTC/GMT的午夜）开始所经过的秒数（不考虑闰秒）*

`运行天数 = round((当前时间 -  网站创建时间)/86400)`

网站创建时间：2025-06-27 00:15  =  1750954500  

```php
<footer id="footer" role="contentinfo " style="line-height: 0.4;">  
    &copy; <?php echo date('Y'); ?> <a href="<?php $this->options->siteUrl(); ?>"><?php $this->options->title(); ?></a>.
    <?php _e('由 <a href="https://typecho.org">Typecho</a> 强力驱动'); ?>.
<div class="stats-container" style="margin: 5px 0;">
            <p>本站已运行 <?php echo round((time() - 1750954500) / 86400); ?> 天</p>
            <?php $this->widget('Widget_Stat')->to($stat); ?>
        </div>
 <p style="margin-top: 5px 0; font-size: 14px; color: #666;">
    备案号：<a href="http://www.miitbeian.gov.cn" target="_blank">豫ICP备2023035002号-1</a>
   </p>
</footer><!-- end #footer -->
```

- `style="line-height: 0.4;`用于调整行间距，默认间距太大，不美观

最终效果如下：

<img src="./assets/image-20250706162834216.png" alt="image-20250706162834216" style="zoom: 50%; " />

#### 调整字号

`./usr/themes/default/style.css`

默认字号略小，修改下面的font-size

```php
.post-content, .comment-content {
  line-height: 1.5;
  word-wrap: break-word;
  font-size:17px;
}
```

#### 字体

`./usr/themes/default/style.css`

- 下载喜欢的字体**仓耳今楷**，下载位置自定义，我这里的相对路径`fonts/canger.woff2`和style.css位于同一目录下，绝对路径就随便写

- 转换为woff2格式，修改``./usr/themes/default/style.css``，把新字体的定义加到最前面

  ```php
  @font-face {
  	font-family: 'canger';
  	src: url('fonts/canger.woff2') format('woff2'),
  		   url('fonts/canger.woff') format('woff'),
         url('fonts/canger.ttf')format('ttf'),
         url('fonts/canger.otf')format('otf');
  	font-weight: normal;
  	font-style: normal;
  }
  ```

- font-family 里有很多字体，越在前面优先级越高，把canger放在最前面

  ```php
  body {
    background-color: #FFF;
    color: #444;
    /*font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;*/
    font-family: "canger", "Droid Serif", Georgia, "Times New Roman", "PingFang SC", "Hiragino Sans GB", "Source Han Sans CN", "WenQuanYi Micro Hei","Microsoft Yahei", serif;
    font-size: 100%;  # 缩放比例
  }
  h1, h2, h3, h4, h5, h6 {
    font-family: "canger", "Helvetica Neue", Helvetica, Arial, "PingFang SC", "Hiragino Sans GB", "WenQuanYi Micro Hei","Microsoft Yahei", sans-serif;
  }
  ```

  

保存以后刷新网页，字体包比较大，一般要等一会才加载出来。这一点应该可以改进。

