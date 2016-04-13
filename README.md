# Common-code
咱七杂八的问题与解决方案

1、去掉chrome浏览器中input或textarea在得到焦点时出现黄色边框的方法  
input,button,select,textarea{ outline:none;}
----------------------------------------------------------------------------------------------------------------------
2、去除火狐和chorme中input或textarea自动拉伸 
 input,button,select,textarea{ resize:none;}
----------------------------------------------------------------------------------------------------------------------
3、兼容性 fixed
.retop{ position:fixed; right:110px; bottom:84px;}
* html .retop{position:absolute;top:expression(eval(document.documentElement.scrollTop+document.documentElement.clientHeight-this.offsetHeight-(parseInt(this.currentStyle.marginTop,10)||0)-(parseInt(this.currentStyle.marginBottom,10)||0))); margin-bottom:100px}
html {
_background-image: url(about:blank);
_background-attachment: fixed; /* prevent screen flash in IE6 */
}  
----------------------------------------------------------------------------------------------------------------------
4、滤镜
opacity: 0.9;filter:alpha(opacity=90);
----------------------------------------------------------------------------------------------------------------------
5、强制英文换行/不换行
(换行)word-wrap: break-word;word-break: normal;  
(不换行）
语法：
white-space : normal | pre | nowrap
取值：
normal : 默认值。默认处理方式。文本自动处理换行。假如抵达容器边界内容会转到下一行
pre : 换行和其他空白字符都将受到保护。这个值需要IE6+或者 !DOCTYPE 声明为 standards-compliant mode 支持。如果 !DOCTYPE 声明没有指定为 standards-compliant mode ，此属性可以使用，但是不会发生作用。结果等同于 normal 。参阅 pre 对象
nowrap : 强制在同一行内显示所有文本，直到文本结束或者遭遇 br 对象。参阅 noWrap 属性 
----------------------------------------------------------------------------------------------------------------------
6、webkit内核中的一些私有的meta标签，这些meta标签在开发webapp时起到非常重要的作用
(http://www.rtfkige.cn/thread-8486-1-1.html) 
       (1)<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0, user-scalable=0" name="viewport" />
       (2)<meta content="yes" name="apple-mobile-web-app-capable" />
       (3)<meta content="black" name="apple-mobile-web-app-status-bar-style" />
       (4)<meta content="telephone=no" name="format-detection" />
        第一个meta标签表示：强制让文档的宽度与设备的宽度保持1:1，并且文档最大的宽度比例是1.0，且不允许用户点击屏幕放大浏览；尤其要注意的是content里多个属性的设置一定要用分号+空格来隔开，如果不规范将不会起作用。
        第二个meta标签是iphone设备中的safari私有meta标签，它表示：允许全屏模式浏览；
        第三个meta标签也是iphone的私有标签，它指定的iphone中safari顶端的状态条的样式；
        第四个meta标签表示：告诉设备忽略将页面中的数字识别为电话号码

<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />

a、width : 控制viewport的大小，可以指定一个值，如600， 或者特殊的值，如device-width为设备的宽度（单位为缩放为100%的CSS的像素）

b、height : 和width相对应，指定高度

c、initial-scale : 初始缩放比例，页面第一次加载时的缩放比例

d、maximum-scale : 允许用户缩放到的最大比例，范围从0到10.0

e、minimum-scale : 允许用户缩放到的最小比例，范围从0到10.0

f、user-scalable : 用户是否可以手动缩放，值可以是：①yes、 true允许用户缩放；②no、false不允许用户缩放

g、target-densitydpi

一个屏幕像素密度是由屏幕分辨率决定的，通常定义为每英寸点的数量（dpi）。Android支持三种屏幕像素密度：低像素密度，中像素密度，高像素密度。一个低像素密度的屏幕每英寸上的像素点更少，而一个高像素密度的屏幕每英寸上的像素点更多。Android Browser和WebView默认屏幕为中像素密度。

下面是 target-densitydpi 属性的 取值范围

device-dpi –使用设备原本的 dpi 作为目标 dp。 不会发生默认缩放。
high-dpi – 使用hdpi 作为目标 dpi。 中等像素密度和低像素密度设备相应缩小。
medium-dpi – 使用mdpi作为目标 dpi。 高像素密度设备相应放大， 像素密度设备相应缩小。 这是默认的target density.
low-dpi -使用mdpi作为目标 dpi。中等像素密度和高像素密度设备相应放大。
<value> – 指定一个具体的dpi 值作为target dpi. 这个值的范围必须在70–400之间。
1	<!-- html document -->
2	<meta name="viewport" content="target-densitydpi=device-dpi" />
3	<meta name="viewport" content="target-densitydpi=high-dpi" />
4	<meta name="viewport" content="target-densitydpi=medium-dpi" />
5	<meta name="viewport" content="target-densitydpi=low-dpi" />
6	<meta name="viewport" content="target-densitydpi=200" />
 
为了防止Android Browser和WebView 根据不同屏幕的像素密度对你的页面进行缩放，你可以将viewport的target-densitydpi 设置为 device-dpi。当你这么做了，页面将不会缩放。相反，页面会根据当前屏幕的像素密度进行展示。在这种情形下，你还需要将viewport的width定义为与设备的width匹配，这样你的页面就可以和屏幕相适应。

----------------------------------------------------------------------------------------------------------------------
7 、去除iphone button 恶心的大圆角：

-webkit-appearance:button;

-webkit-appearance: none;(去除input阴影) 
----------------------------------------------------------------------------------------------------------------------
8、很正常的页面，到了webkit怎么就变样了呢好吧你需要折行代码
<style>
html{-webkit-text-size-adjust:none;}
</style>
----------------------------------------------------------------------------------------------------------------------
9、http://www.bootcss.com/ 神级框架 
----------------------------------------------------------------------------------------------------------------------
10、ie6png透明，妥妥的(此方法不支持sprite，慎用)
_FILTER:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='images/fouc_ico1.png');_background:none; 
----------------------------------------------------------------------------------------------------------------------
11、onmouseout 冒泡事件，这玩意很普通了，但是很常用，备个案在这。
function isMouseLeaveOrEnter(e, handler) {  
            if (e.type != 'mouseout' && e.type != 'mouseover') return false;  
            var reltg = e.relatedTarget ? e.relatedTarget : e.type == 'mouseout' ? e.toElement : e.fromElement;  
            while (reltg && reltg != handler)  
                {reltg = reltg.parentNode;  }
            return (reltg != handler);
        }使用方法：
        object.onmouseover=function alertMe(e,f){
            if (isMouseLeaveOrEnter(e,f))
            {
                alert(f)
            }
        } 

或者
function test(obj, e) {
if (e.currentTarget) {
   if (e.relatedTarget != obj) {
    if (obj != e.relatedTarget.parentNode) {
     alert(1);
    }
   }
} else {
   if (e.toElement != obj) {
    if (obj != e.toElement.parentNode) {
     alert(1);
    }
   }
}
}

或者
jq中的
mouseleave
---------------------------------------------------------------------------------------------------------------------- 
12、input里面的字focous后没了，你懂得...
placeholder="";
---------------------------------------------------------------------------------------------------------------------- 
13、Jquery常用动画
http://www.w3school.com.cn/jquery/jquery_effects.asp 
----------------------------------------------------------------------------------------------------------------------
14、css 中文字体的英文标示，宋体的英文-黑体的英文-中文字体的英文名称：
黑体：SimHei
宋体：SimSun
新宋体：NSimSun
仿宋：FangSong
楷体：KaiTi
仿宋_GB2312：FangSong_GB2312
楷体_GB2312：KaiTi_GB2312  
微软雅黑体：Microsoft YaHei
---------------------------------------------------------------------------------------------------------------------- 
15、Div内容垂直居中,思路是模拟table利用vertical-align
      <div style="display:table">
            <div style="display:table-cell;vertical-align:middle;">
      ***********
           </div>
      </div>

16、一个响应式测试网站 http://www.mattkersley.com/responsive/
 
17、jquery  siblings  获取所有同胞元素，$('li.third-item').siblings().css('background-color', 'red');
18、手机屏幕：console.log(screen.availWidth;);
     @media only screen and (min-width: 400px) and (max-width: 1024px) 当页面大于400小鱼1024
---------------------------------------------------------------------------------------------------------------------- 
19、循环中的闭包
for(var i=0;i<**;i++)
{
    (function(i){
    //run
    })(i);
} 
---------------------------------------------------------------------------------------------------------------------- 
20、get Url Param  （jquery$.getUrlParam('')）
function getUrlParam(name){  
    //构造一个含有目标参数的正则表达式对象  
    var reg = new RegExp("(^|&)"+ name +"=([^&]*)(&|$)");  
    //匹配目标参数  
    var r = window.location.search.substr(1).match(reg);  
    //返回参数值  
    if (r!=null) return unescape(r[2]);  
    return null;  
}  

----------------------------------------------------------------------------------------------------------------------
21、什么px,pt,em,rem 怎么换算
http://pxtoem.com/ 看这个 
----------------------------------------------------------------------------------------------------------------------
22、手机中的几个事件
obj.addEventListener("touchstart",function(e){ //开始触摸
      var even = e || window.event;//获取obj
      even .preventDefault();//清除其他元素滚动
      stratX =even .changedTouches[0].pageX //触摸开始时候的X坐标
      addEventListener("touchmove",function(e){...},false); //滑动触摸
      addEventListener("touchmove",function(e){...},false); //结束触摸
},false);
----------------------------------------------------------------------------------------------------------------------
23、关于占位符
 &#32; == 普通的英文半角空格   
&#160; == &nbsp; == &#xA0; == no-break space （普通的英文半角空格但不换行）  
&#12288; == 中文全角空格 （一个中文宽度）  
&#8194; == &ensp; == en空格 （半个中文宽度）   
&#8195; == &emsp; == em空格 （一个中文宽度）  
&#8197; == 四分之一em空格 （四分之一中文宽度）
-----------------------------------------------------------------------------------------------------------------------
24、手机回弹效果：-webkit-overflow-scrolling : touch;  
-----------------------------------------------------------------------------------------------------------------------
25、jsonp 乱码？ scriptCharset:"gbk"  







