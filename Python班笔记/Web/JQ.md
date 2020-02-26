## JQ

### jq导入

```python
$ = JQuery,意思就是把$符号换成JQuery也可以
$(css选择器) ：格式是这样的，获取一个标签

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        #zz{
            width: 800px;
            height: 800px;
            background-color: red;
        }

    </style>
</head>
<body>
    <div class="box">好好学习天天向上</div>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        // 我们之前学的js获取div
        var box = document.querySelectorAll('.box')[0];
        box.setAttribute('id', 'zz');
        console.log(box.innerHTML);  // 好好学习天天向上

        // 利用jq获取div,方便很多
        console.log($('.box').text()); // 好好学习天天向上
    </script>
</body>
</html>


以下这样放在head标签里面也可以生效格式 : $(function () {
            
        })
<script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        $(function () {
            alert('zzzzz')
        })
    </script>
```

### 元素选择

```python
基本选择器：标签选择器$('p')，id选择器$('#id名')，class选择器$('.class名')
层级选择器：子代$('父亲标签>儿子标签')，后代$('父亲标签 后代标签')，相邻$('pre+next')后面的一个，兄弟$('pre~next')后面的全部
```

```python
筛选器：
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <div>元素1</div>
    <div>元素2</div>
    <div>元素3</div>
    <h3>以下为children</h3>
    <div class="box">
        <span>无class</span> <br>
        <span class="test">有class</span> <br>
        <p>无class</p>
        <p class="test">有class</p>
        <div>无class</div>
        <div class="test">有class</div>
        <div id="zz">有id</div>
    </div>
    <h3>以下为parent</h3>
    <div class="div1">div1
        <div class="div2">div2
            <div class="div3">div3
                <div class="div4">div4
                    <div class="div5">div5
                        <div class="div6">div6
                            <div class="div7">
                                div7
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <h3>以下是sibling</h3>
    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div>
    <div class="box4">4</div>
    <div class="box4">5</div>
    <script>
        // first,last,eq
        // $('div').first().css('font-size','30px');  // 修改样式，注意是逗号隔开，第一个
        // $('div').last().text('ok');  // 修改元素文本内容，最后一个
        // $('div').eq(0).css('color', 'skyblue');  // eq里面填元素的索引值，指定元素

        // children,find:类似于后代选择器，children可以不带参数
        // $('.box').children().css('color', 'skyblue');  // 选中所有的儿子
        // $('.box').children('.test').css('font-size', '30px');  // 筛选子代class名为test的标签

        // find的用法，必须带参数
        // $('.box').find('#zz').css('font-size', '30px');
		
        // parent,parents,parentsUntil
        // parent
        $('.div5').parent().css('color', 'yellow'); // 渲染了4567，可以操作的是唯一父级和全部子级！也就是只能拿上面的爸爸
        // parents 修改祖先元素以及后代所有的
        $('.div5').parents().css('font-size', '25px');
        // parentsUntil 要带参数,参数是.div2选中的就是.div3到后面所有
        $('.div5').parentsUntil('.div2').css('color', 'skyblue');

        // sibling：找到全部的同级元素,自己不变
        $('.box2').siblings().css('color', 'red');
    </script>
</body>
</html>
```

```python
区别，筛选器的优势，在函数中会更容易实现。
简单操作时随便用哪个都可以，用函数的时候用筛选器会方便的多

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        ul{
            list-style: none;
        }
    </style>
</head>
<body>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <ul>
        <li>足球</li>
        <li>篮球</li>
        <li>乒乓球</li>
    </ul>
    <script>
        // 选择器，简化eq选择的写法
        $('li:eq(2)').css('color', 'skyblue');  // 这里是选择器

        //  这里是筛选器
        $('li').eq(0).css('color', 'red'); // 筛选器

        // 在函数中可以看出筛选器的优势，不用字符串拼接那么麻烦
        // 这里obj就是$选中的标签，index就是下标
        function f(obj, index) {
            obj.eq(index).css('color', 'red')
        }
        f($('li'), 2)
    </script>
</body>
</html>
```

### 元素操作，属性操作+css样式操作+标签处理+事件

#### 一，属性操作，三类：

1，text()   2,html()    3,val()

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div>1 <span>你好</span> </div>
    <div>2</div>
    <input type="text" name="user"> <br>
    <input type="password" name="password"> <br>
    <input class="btn" type="button" name="btn" value="获取value值"> <br>

    <h3>属性操作</h3>
    <ul>
        <li>足球</li>
        <li>篮球</li>
        <li>棒球</li>
    </ul>

    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        // html(),有多个元素的时候拿到的时第一个，把标签名都取到
        console.log($('div').html());  // 1 <span>你好</span>,有多个元素的时候拿到的时第一个

        // text(),符合的元素的文本内容都取到
        console.log($('div').text()); //  1 你好 2

        // val(),多个元素的话只取第一个
        $('.btn').click(function () {
            console.log($('input').val())
        });
    </script>
</body>
</html>
```

2，属性操作attr， 删除属性removeAttr， 

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div>1 <span>你好</span> </div>
    <div>2</div>
    <input type="text" name="user"> <br>
    <input type="password" name="password"> <br>
    <input class="btn" type="button" name="btn" value="获取value值"> <br>

    <h3>属性操作</h3>
    <ul>
        <li>足球</li>
        <li>篮球</li>
        <li>棒球</li>
    </ul>

    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        // 属性操作，属性的增删改查
        $('li').attr('class', 'test');  // 增加了名为test的类属性，也可以用来修改
        // 查
        console.log($('li').attr('class'));
        // 删除
        $('li').removeAttr('class');
    </script>
</body>
</html>
```

3，addClass   /   removeClass   /   toggleClass，  Class可以替换为任何属性

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .p1{
            color: #4e3f80;
            font-size: 30px;
        }
    </style>
</head>
<body>
    <div>1 <span>你好</span> </div>
    <div>2</div>
    <input type="text" name="user"> <br>
    <input type="password" name="password"> <br>
    <input class="btn" type="button" name="btn" value="获取value值"> <br>

    <h3>属性操作</h3>
    <ul>
        <li>足球</li>
        <li>篮球</li>
        <li>棒球</li>
    </ul>

    <h3>class操作</h3>
    <p>我是一段文字</p>
    <button>addclass</button>
    <button>removeclass</button>
    <button>toggleclass</button>

    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        //  class属性操作
        // addClass   /   removeClass   /   toggleClass 切换样式
        $('button').eq(0).click(function () {
            $('p').addClass('p1')
        });
        $('button').eq(1).click(function () {
            $('p').removeClass('p1')
        });
        $('button').eq(2).click(function () {
            $('p').toggleClass('p1')
        });
    </script>
</body>
</html>
```

#### 二，css样式操作

1,css()

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            width: 200px;
            height: 200px;
            background-color: #4c5bed;
            border: 1px solid rgb(11,23,55);
        }
    </style>
</head>
<body>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <div>我就是我</div>
    <script>
        // 获取单个样式
        console.log($('div').css('background-color'));  // 通过这个方式获取css的样式属性值 rgb(76, 91, 237)

        // 获取多个样式,用列表括起来
        console.log($('div').css(['background-color', 'width', 'height']));

        // 设置
        // $('div').css('font-size', '30px');  // 单个设置
        // 设置多个对象
        $('div').css({  // 这里用的是json
            "font-size": '30px',
            'background-color': 'yellow',
            "text-align": 'center',
            'line-height': '200px',
        });
    </script>
</body>
</html>
```

2,offset() , position() , scrollTop,  scrollLeft

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            width: 200px;
            height: 200px;
            background-color: #4c5bed;
            border: 1px solid rgb(11,23,55);
        }
        .one{
            background-color: #a7ff6b;
            position: relative;
        }
        .two{
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
            top: 20px;
            left: 20px;
        }
        .three{
            margin-top: 100px;
            width: 100px;
            height: 100px;
            overflow: auto;
        }
    </style>
</head>
<body>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <div>我就是我</div>
    <h3>下面是offset, position</h3>
    <div class="one">
        <div class="two">
            测试对象
        </div>
    </div>

    <div class="three">
        层级选择器：子代$('父亲标签>儿子标签')，后代$('父亲标签 后代标签')，相邻$('pre+next')后面的一个，兄弟$('pre~next')后面的全部
    </div>
    <button>获取scrolltop</button>
    <button>设置scrolltop</button>
    <script>
        // 位置设置offset() , position() , scrollTop,  scrollLeft
        // offset()距离窗口的位置,top,left值
        // 这里加$提示自己这是一个jq对象
        var $obj = $('.two').offset();
        console.log($obj);  // {top: 273.4375, left: 9}
        console.log($obj.left);
        console.log($obj.top);

        // position(),得到的结果是自己设置的
        var $obj1 = $('.two').position();
        console.log($obj1);  // 这里是到父级div的距离
        console.log($obj1.top);
        console.log($obj1.left);

        // scrollTop / height / width
        $('button').eq(0).click(function () {
            alert($('.three').scrollTop()+'px');  // 滑块到上面的距离
            alert($('.three').height()+'px');
            alert($('.three').width()+'px');
        });
        $('button').eq(1).click(function () {
            $('.three').scrollTop(100);  // 直接写值可以设置
            $('.three').height(200);  // 直接写值可以设置
            $('.three').width(100);  // 直接写值可以设置
        });

    </script>
</body>
</html>
```

#### jq和js对象的转换

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div>元素一</div>
    <div>元素二</div>
    <div class="three">元素三</div>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        // jq ==> js
        // 1,
        var $div = $('div');  // 这个是jq对象
        var div = $div[0]; // 转换为js对象
        div.style.color = 'red';  // js里操作元素的方法

        // 通过jq自带的get方法
        var div1 = $div.get(1);  // 一样用下标
        div1.style.color = 'blue';

        // js ==> jq
        var box = document.querySelectorAll('div'); // js对象
        var $box = $(box); // 通过$包一下就成了jq对象
        $box.eq(2).css('font-size', '30px');

        // this,表示的就是这个自己选中的对象
        var three = document.querySelector('.three');
        three.onclick = function () {
            console.log(this);
        };

        // jq获取对象，可以利用这个this来做一系列的属性操作等等。
        var $three = $('.three');
        $three.click(function () {
            var $thins = $(this);
            $thins.css('color', 'yellow');
        });
    </script>
</body>
</html>
```

### 标签处理

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <div class="div1">
        <div class="div2">div2</div>
        <div class="div3">div3</div>
        <div class="div4">div4</div>
        <div class="div5">div5</div>
    </div>
    <script>
        // 内部插入:append(),appendTo(),prepend(),prependTo()
        // append,添加标签在目标元素的内容后面
        // $('.div3').append('<p style="color: red">append</p>');
        // prepend，插在指定元素的内容前面
        // $('.div3').prepend('<p>"择天记"</p>');
        // appendTo 位置需要调换
        // $('<p>appendTo</p>').appendTo($('.div4'));
        // prependTo,同理
        // $('<p>prependTo</p>').prependTo($('.div4'));

        // 外部插入:before()/insertBefore()/after()/insertAfter()/replaceWith()/remove()/empty()/clone()
        // after,放在标签后面，不在里面了噢！
        $('.div4').after('<p>after</p>');
        // before,放在标签前面
        $('.div4').before('<p>before</p>');
        // insertBefore，顺序反过来
        $('<p>insertBefore</p>').insertBefore($('.div5'));
        // insertAfter
        $('<p>insertAfter</p>').insertAfter($('.div5'));
        // replaceWith 替换内容和标签
        $('.div3').replaceWith('<p>我是来替换div3的</p>');
        //remove  直接把标签和内容都清除
        $('.div2').remove();
        //empty  只清空内容，不清除标签
        $('.div4').empty();
        // clone  复制
        $('.div5').clone().appendTo($('p'));
    </script>
</body>
</html>
```

### 事件

```python
each的用法，功能跟for一样，方便很多

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        ul{
            list-style: none;
        }
        li{
            height: 20px;
            width: 20px;
            background-color: #4c5bed;
            float: left;
            border-radius: 50%;
            margin-left: 20px;
        }
    </style>
</head>
<body>
    <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </ul>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        // each 遍历，功能跟for一样
        $('li').each(function (index) {
            console.log(index); // 0 1 2 3
        });

        // for循环绑定事件,这是js的用法
        // var li = document.querySelectorAll('li');
        // for (let i=0;i<li.length;i++){
        //     li[i].onclick = function () {
        //         alert(i);
        //     }
        // }

        // each方法,自己写出来的，值得嘉许
        $('li').each(function (index) {
            $('li').eq(index).click(function () {
                alert(index)
            })
        })
        
         // index(),内置的方法
        $('li').click(function () {
            console.log($(this).index())
        })
    </script>
</body>
</html>
```

### 鼠标移入移出

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            width: 100px;
            height: 100px;
            background-color: #4c5bed;
        }
    </style>
</head>
<body>
    <div>我就是我</div>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        // 鼠标移入移出
        var $div = $('div');
        // $div.hover(f1, f2); // 可以放两个函数，第一个鼠标移入函数，第二个移出函数
        $div.hover(function () {
            console.log('我是移入')
        },function () {
            console.log('我是移出')
        })

    </script>
</body>
</html>
```

### 动画

动画一

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            height: 200px;
            width: 200px;
            background-color: skyblue;
        }
    </style>
</head>
<body>
    <div class="box"></div>
    <button>隐藏</button>
    <button>显示</button>
    <button>切换</button>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
        // 隐藏和显示,自己写出来的值得嘉许
        var $box = $('.box');
        var $btn = $('button');
        $btn.eq(0).click(function () {
            $box.hide(2000);
        });
        $btn.eq(1).click(function () {
            $box.show(2000);
        });
        $btn.eq(2).click(function () {
            $box.toggle(2000);
        });
    </script>
</body>
</html>
```

动画二

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .div{
            width: 200px;
            height: 200px;
            background-color: #4c5bed;
        }
        .div1,.div2,.div3{
            width: 100px;
            height: 100px;
            /*background-color: red;*/
        }
    </style>
</head>
<body>
    <div class="div">
        <div class="div1" style="background-color: #4b1280"></div>
        <div class="div2" style="background-color: #a7ff6b"></div>
        <div class="div3" style="background-color: darkred"></div>
    </div>
    <div style="margin-top: 200px"><button>fadeTo</button></div>
    <div class="box4"  style="width: 200px;height: 200px;background-color: green;display: none">
        <h3>标题</h3>
        <p>段落一</p>
        <p>段落二</p>
    </div>
    <div class="box5">
        <button>slidedown</button>
        <button>slideup</button>
        <button>slidetoggle</button>
    </div>
    <div class="box6">
        <button>自定义动画1</button>
        <button>自定义动画2</button>
    </div>
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
    <script>
    $('button').click(function () {
        $('.div1').fadeTo('slow', 0.3);
        $('.div2').fadeTo('slow', 0.7);
        $('.div3').fadeTo('slow', 0.1);
    });

    // 滑动
    var $btn = $('.box5>button');
    $btn.eq(0).click(function () {
        $('.box4').slideDown('slow');
    });
    $btn.eq(1).click(function () {
        $('.box4').slideUp('slow')
    });
    $btn.eq(2).click(function () {
        $('.box4').slideToggle('quick')
    });

    // 自定义动画 animate
    var $box6 = $('.box6>button');
    $box6.eq(0).click(function () {
        $('.div').animate({height:'300px'}).delay(5000)  // 这里的延迟是延迟5s后，再发生下一个变化
    });
    $box6.eq(1).click(function () {
        $('.div').animate({height:'200px'})
    })
    </script>
</body>
</html>
```

