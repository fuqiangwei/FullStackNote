---
Author: fuqiangwei
Date:   2015-12-24 01:14:17
Last Modified by:   fuqiangwei
Last Modified time: 2015-12-28 10:31:30
---

##  css3core

2、属性选择器
   将元素属性用于选择器中，从而获取指定元素属性或者值得元素
   语法：
       [属性] : 具备 指定属性 的所有元素全部匹配出来
       元素[属性] : 匹配具备 属性的 指定元素
          p[id] : 匹c配具备id属性的p元素
          div[class] :
       元素[属性1][属性2] :
         p[id][class] : 匹配出所有即具备id属性，又具备class属性的p元素
       元素[属性=值] :
          input[type="text"] : 匹配type的值为text的input元素
       元素[属性~=值] :
          input[class ~= second] :
      <input class="first second" />
      <input class="myseconddiv" />

      ~= : 包含指定的数据（独立）
      =  : 只有指定的数据
       元素[属性^=值] : 匹配指定属性以指定值开始的指定元素
          p[class^=f] : 匹配class以f开始的p元素
    <p class="first"></p>可以匹配
    <p class="fast"></p>可以匹配
    <p class="second"></p>不能匹配
       元素[属性*=值] : 属性包含值元素
          p[class*="valid"];
    <p class="myvalid"></p>
       元素[属性$=值] : 匹配属性以指定值结束的元素
       元素[属性!=值] : 匹配属性不等于具体值得元素

   eg:
      input[id] : 获取具备id属性的input元素
      <input type="text" />
      <input type="radio" id="rdoGender" />

练习2:
  过 .....
=============================================
1、伪类选择器
   回顾：什么是伪类选择器
         更改元素的不同的状态的样式
   :hover :link :visited :active
   1、目标伪类
      1、什么是目标伪类
         突出显示活动的HTML锚，用于选取当前活动的目标元素
      2、语法
         :target
   p:target
   2、元素状态伪类
      1、什么是元素状态伪类
         主要匹配元素的禁用、启用、选中状态
         多数应用在表单元素上
      2、常用的状态伪类
         :disabled  匹配每个被禁用的元素
   :enabled 匹配每个已启用的元素
   :checked 匹配每个被选中的元素(只用于单选按钮和复选框)
   3、结构伪类
      1、什么是结构伪类
         主要从元素的结构(层级结构)上来进行划分的
      2、什么时候使用结构伪类
         找 第一个子元素、最后一个子元素、没有子元素、仅仅只包含一个子元素 优先使用结构伪类
      3、如何使用结构伪类
         :first-child  匹配属于其父元素的首个子元素
   :last-child 匹配属于其父元素的最后一个子元素
   :empty 匹配没有子元素(包含文本)的元素
     <p>这是一个段落</p> 非empty
     <div></div> empty
   :only-child 匹配属于其父元素的唯一子元素
     <div>
       <span></span>
       <span></span>
     </div>
     <div>
       <span></span>
     </div>

   4、否定伪类
      匹配非指定元素/选择器的每个元素
      语法:
           :not(selecotr)
      eg:
        1、获取 input 但是 type不是text的所有元素
     input[type=text]
     input:not([type=text])
  2、获取除第一个div子元素意外的其他div子元素
     div:first-child
     div:not(div:first-child)
2、伪元素选择器
   主要针对元素中的文本内容进行匹配的。
   1、:first-letter
      选取指定选择器的首字母
      eg:
        p:first-letter{

  }
      一般用于 排版、首字符突出等操作
   2、:first-line
      选取指定选择器的首行
   3、::selection
      匹配用户选取的部分

=================================================
1、内容生成
   1、什么是内容生成
      通过css 向元素的前面或后面增加一部分内容
   2、伪元素
      :before 匹配到某一元素的最前面
          p:before
      :after 匹配到某一元素的最后面
          p:after
   3、内容生成
      content : 配合 :before 或 :after伪元素，插入生成内容
      content的常用取值:
      1、字符串:纯文本，插入到指定的位置处
         p:before{
    content:"至尊宝:";
   }
      2、url:生成的图像
         a:before{
    content:url(Images/i1.jpg);
   }
      3、计数器
2、计数器
   1、计数器的作用
      向已存在的html文本内容增添序号
   2、如何使用计数器
      1、定义计数器
         属性:counter-reset
   作用:定义一个计数器，并且设置初始值为0
   body{
    counter-reset:计数器名称 初始值 计数器名称 初始值;
   }
   body{
    counter-reset:count 10;
   }

      2、设置计数器增量
         可以单独设置某一选择器使用计数器时的增量，默认值是1
   属性:counter-increment
         div{
    counter-increment:count 10;
   }
      3、使用计数器
         通过 counter(计数器名称) 来使用计数器
   div:before{
    content:"第"counter(count)"章";
   }
3、多列
   1、分隔列
      把一段文本拆分成几列
      column-count:规定元素被分隔的列数
   2、列间隔
      设置列与列之间的距离
      column-gap:间隔;
   3、列规则
      可以在列与列之间设置一条间隔线，列规则可以设置间隔线的样式、颜色、粗细
      column-rule:大小 样式 颜色;

      column-rule-width:
      column-rule-style:
      column-rule-color:
   4、浏览器兼容
      1、IE10 以及 Opera 浏览器支持多列属性
      2、FireFox 需使用前缀 -moz-
         -moz-column-count:
   -moz-column-gap:
   -moz-column-rule:
      3、Chrome 和 Safari
         -webkit-column-count:
   -webkit-column-gap:
   -webkit-column-rule:
4、CSS Hack
   1、为什么需要CSS Hack
      浏览器兼容性所引发的问题

   2、浏览器运行模式
      1、混杂模式
      2、标准模式(Standard Mode)
      3、准标准模式(Almost Standard Mode)
   3、浏览器主要通过 DOCTYPE 进行模式选择
      触发混杂模式:不声明DOCTYPE
      触发标准模式:

   4、浏览器兼容问题
      1、margin和padding
         ie6中 默认的 maring 偏大
   解决方案:body{margin:0px;}
      2、居中布局
         ie6以及低版本浏览器:通过父元素的text-align:center;完成居中
   高版本浏览器(ie6,ie7+,chrome,firefox,opera,safari):通过当前元素的margin实现即 margin:0 auto;
      3、元素高度与内容
         ie6 : 元素的高度至少包括内容
   其他:元素高度会超出容器
   解决方案:overflow属性
      4、子元素设置上外边距时
         ie6:正常显示
   其他版本:子元素的上外边距会认为是父元素的上外边距
   解决方案:
      1、给父元素设置边框
      2、设置父元素的 padding-top

   5、HTML头部引用Hack
      通过HTML条件注释完成
      <!--[if 条件]>
      <![endif]-->

      IE6:
         <!--[if IE 6]>
     编写HTML
     引入css
   <![endif]-->
      大于IE6的版本:
      <!--[if gt IE 6]>
      <![endif]-->

1、变形 - transform 迅速变化
2、过渡 - transition 缓慢变化
3、动画 - animation 关键帧动画


1、转换原点
   默认情况下，原点是在当前物体的中心点上
   修改原点:
     属性:transform-origin
     值:
         1、x坐标  y坐标
      当前物体的左上点为 x:0 y:0
   2、宽度百分比 高度百分比
      0%   0% 左上点
      50% 50% 中心点
   3、关键字
      top:上
      bottom:下
      left:左
      right:右
      center:中间
      center center
      left top
    transform-origin:0; 表示 所有轴的位置都将归到0点处
    transform-origin:50px 50px; 表示 x轴在50像素处，y轴在50像素处
    transform-origin:50px 50px 50px; 表示 x轴，y轴，z轴
2、变形:2d
   旋转:rotate()
   位移:translate()
   缩放:scale()
   倾斜:skew()

   旋转:围绕一个参照原点(transform-origin),旋转指定角度，默认为顺时针
   语法:transform:rotate(ndeg);
        n为正 则按顺时针旋转
  n为负 则按逆时针旋转
   注意:rotate在旋转的过程中，不但能够旋转元素，同时能够旋转绘图的坐标系方向。如果配合着其他的变形一起来做的话，rotate在前的话，会影响之后延坐标轴的其他变形。
   解决方案:如果配合变形一起来做，最好将rotate放在最后一个函数上

   位移:延 坐标方向 移动指定的距离
   语法:translate(x轴移动距离,y轴的移动距离);
        x : 正为右，负为左
  y : 正为下，负为上

  transform:translate(50px,50px);
   注意:位移不会影响其他元素位置,单可能会盖住周围元素
   其他两个单方向位移:
        translateX(距离);
  translateY(距离);

   缩放:将指定坐标轴上的坐标缩放指定的倍数
   语法:scale(倍数)
        倍数 : 0-1 之间的小数,缩小
         >1 放大
  scale(倍数) 表示等比缩放
   其他两个单方向缩放:
        scaleX(倍数);
  scaleY(倍数);
   transform:scale(2);

   倾斜:沿着坐标轴方向，倾斜指定角度
   语法:skew(ndeg);仅沿x轴倾斜
        skew(ndeg,ndeg);沿着x轴和y轴同时倾斜
   单方向倾斜:
        skewX(ndeg)
  skewY(ndeg)
   x轴方向:角度为正，向左倒
           角度为负，向右倒
   y轴方向:角度为正向上倾斜
           角度为负向下倾斜

3、3d变形
   元素,要从立体角度观察
   坐标轴,x轴，y轴，z轴

   属性:
      perspective
      设定假定的人眼位置到投影平面的距离
      如何使用：设置在父元素上的
      浏览器兼容性:
       Chrom,Safari : -webkit-perspective
       Firefox : -moz-perspective
   位移:
       3D位移可以改变元素在z轴上的位置
       translateZ(z);
       translate3d(x,y,z);
   旋转:
  transform:
       rotateX(ndeg);
       rotateY(ndeg);
       rotateZ(ndeg);
   缩放:
       transform:
           scaleZ(z);
     scale3d(x,y,z);
==================================================
1、过渡
   transition
   1、什么是过渡
      CSS属性在一段时间内进行平滑的过渡
   2、过渡四要素
      1、过渡属性:background,color,transform
      2、过渡所需时间:
      3、过渡函数:速度和方式
      4、过渡延迟时间:激发操作后的执行间隔(s|ms)
   3、过渡属性
      1、过渡属性
         属性名:transition-property
   transition-property:background,color;
      2、过渡时间:
         属性名:transition-duration:
   以秒(s)或毫秒(ms)为单位
   transition-duration:5s;
      3、过渡函数
         属性名:transition-timing-function
   备选值:
        ease:默认值，慢速开始，快速变快，慢速结束
        linear:匀速过渡
        ease-in:慢速开始，加速效果
        ease-out:以慢速结束，减速效果
        ease-in-out:以慢速开始和结束，中间先加速再减速
      4、过渡延迟
         属性名:transition-delay
   以秒或毫秒为单位
      5、整合transition属性
         transition:属性名 持续时间 过渡函数 [延迟],
        属性名 持续时间 过渡函数 [延迟];
2、关键帧动画
   关键帧:动画执行过程中，物体在某一位置上的特殊状态
   关键帧动画:使用连续的关键帧，控制物体联系的状态变化
   什么时候使用关键帧动画:
   1、连续，有规律的过渡 -- 过渡 transition
   2、无规律的连续变化 -- 动画 animation
   如何实现:
   2大步:
   1、定义关键帧
      @keyframes 动画名{
  from{
     0%
     css样式
     动画开始的状态
  }

  percent{

  }

  to{
     100%
     css样式
     动画结束的状态
  }
      }

      @keyframes change{
  from{
    background:red;
  }
  10%
  {
    background:yellow;
  }
  50%
  {
    background:green;
  }
  to
  {
    background:pink;
  }
      }

      浏览器兼容性:
      @keyframes : IE , 火狐
      @-webkit-keyframes : Chrome Safari
      @-o-keyframes : Opera
   2、触发动画(调用动画)
      属性:animation
         animation:动画名 持续时间 速度类型;
   如何:
      1、写在非伪类选择器中，页面加载则执行动画
      2、写在伪类中，伪类触发时则播放动画
      浏览器兼容性:
        -webkit-animation: Chrome，Safari
  -o-animation:Opera
   3、动画子属性
      1、animation-name : @keyframes(动画)名称
      2、animation-duration : 动画时长
      3、animation-timing-function:动画速度函数
      4、animation-delay:动画的延迟时间
      animation:name duration timing-function;
      5、animation-iteration-count : 播放次数
         取值:
     1、具体数值
     2、infinite(无限次播放)
      6、animation-direction : 动画播放方向
         取值:
     1、normal 正常播放
     2、alternate 轮流播放
        奇数次数：正向播放
        偶数次数：反向播放
   animation:name duration timing-function delay iteration-count direction;
      7、animation-fill-mode
         动画播放前后的效果
   备选值:
     1、none:不改变默认行为
     2、forwards:动画完成后保证最后一个属性状态
     3、backwards:动画播放前，显示开始属性值
     4、both
      8、animation-play-state
         控制动画播放与暂停
   备选值:
     1、paused : 暂停动画
     2、running : 播放动画
   使用场合:
     1、配合伪类选择器
     2、结合Javascript使用

@keyframes second{
  from{
    transform:rotate(0deg);
  }
  to{
    transform:rotate(360deg);
  }
}
调用
#second{
  animation:second 60s linear 0s infinite;
}



##  HTML5core


HTML5 DAY01:
 * 基本内容
   * HTML5目前最新的规范(标准)是2014年10月推出
   * 2005年左右出现HTML5版本(非标准)
     * W3C组织(两个组织定义H5规范)
   * 学习(研究)HTML5是学习未来(将来主流)
   * HTML版本 - 第一阶段主要学习还是4版本(包含5版本)
     <header><nav>
   * HTML5版本之后,声明不再出现版本信息
     * 有意地版本,以后可能不再会有新版本
     * HTML5的规范内容实时更新
   * 注意
     * HTML5永远都不可能离开javascript.
     * HTML5在移动端支持好于PC端
 * HTML5新表单
   * input新类型
     * email类型 - 验证是否包含"@"
     * url类型 - 验证是否包含"http://"
     * tel类型 - 只在移动端显示
     * number类型
     * range类型
     * date类型
     * color类型
   * 表单新元素
     * datalist元素
     * progress元素
     * meter元素
     * output元素
   * 表单新属性
     * placeholder - 提供默认提示内容
     * multiple - 允许输入多个值
       * 多个值之间使用","
     * autofocus - 自动获取焦点
     * form - 允许表单元素定义在表单之外
   * 表单新验证
     * 验证属性
       * required属性
         * 验证当前元素值是否为空
       * pattern属性
         * 使用正则表达式验证当前元素值是否匹配
   * 注意 - 并不能验证当前元素值是否为空
       * min和max属性
         * 验证当前元素值最小值或最大值
   * 一般适用于number、range等元素
       * minlength和maxlength属性
         * minlength - 验证当前元素值的最小长度
     * 输入值时,允许输入小于指定值
     * 提交表单时,验证元素值最小长度
     * 注意
       * minlength并不是HTML5新属性
   * maxlength - 验证当前元素值的最大长度
     * 输入值时,长度不能大于指定值
       * validity属性
         * 表单验证HTML5提供一种有效状态
   * 有效状态通过validityState对象获取到
   * validityState对象可通过validity属性得到
     * 验证(有效)状态
       * validityState对象提供了一系列的有效状态
       * 通过这些有效状态,进行判断
       * 注意
         * 所有验证状态必须配合上述的验证属性使用
       * 作用
         * 用来替换原本手工实现的逻辑
       * 验证状态
         * valid
     * 作用 - 判断当前元素值是否正确
     * 注意
       * 该状态返回true,表示验证成功
       * 该状态返回false,表示验证失败
   * valueMissing
     * 作用 - 判断当前元素值是否为空
     * 用法 - 配合required属性使用
   * typeMismatch
     * 作用 - 判断当前元素值的类型是否匹配
     * 用法 - 配合email、number、url等
   * patternMismatch
     * 作用 - 判断当前元素值是否与指定正则表达式匹配
     * 用法 - 配合pattern属性使用
   * tooLong
     * 作用 - 判断当前元素值的长度是否正确
     * 用法 - 配合maxlength属性
     * 注意
       * 使用maxlength属性后,实际不可能出现长度大于maxlength的值
       * tooLong很难出现这种情况
   * rangeUnderflow
     * 作用 - 判断当前元素值是否小于min属性值
     * 用法 - 配合min属性
     * 注意 - 并不能与max属性值进行比较
   * stepMismatch
     * 作用 - 判断当前元素值是否与step设置相符
     * 用法 - 配合step使用
     * 注意 - 并不能与min或max属性值进行比较
   * customError
     * 用法 - 配合setCustomValidity()方法
       * 如果使用该方法,该状态返回true
     * setCustomValidity()方法
       * 作用 - 设置自定义的错误提示内容
       * 问题 - 使用该方法设置错误信息
         * 当输入正确时,调用该方法将信息设置为空("")
         * 不能使用上述有效状态的任何一种判断输入是否正确(所有状态返回false)
 * 扩展内容
   * 代码的编写 - 逻辑的完整性
     * 判断value值是否为空
       value==""||value==null
     * tooLong状态



HTML5 DAY02:
 * 音视频处理
   * 视频处理
     * 基本内容
       * 使用Flash技术处理HTML页面中的视频内容
         * 包含音频、动画、网页游戏等
   * 特点
     * 浏览器原生不支持(IE浏览器要求安装ActiveX组件)
     * 性能不好(不能过多地使用)
     * 智能移动端并不支持Flash技术
   * 命运
     * Flash的母公司Adobe公开宣布放弃
       * 目前用于替代Flash技术最好的选择 - HTML5
         * 几乎所有浏览器原生支持<video>元素
   * 性能更高
   * 智能移动端支持非常好
     * 如何实现视频处理
       * <video>元素
         * 如果当前浏览器不支持<video>元素
     * 在<video>元素内编写提示内容
   * 属性
     * src - 引入视频文件的路径
     * autoplay - 自动播放视频
       * 使用<source>元素
         <video>
      <source src="一种视频格式" />
      <source src="一种视频格式" />
      <source src="一种视频格式" />
   </video>
     * <video>支持的视频格式
       * MP4格式 - 目前比较主流
       * OGG格式 - 多用于移动端
       * WebM格式 - 目前唯一支持超高清格式
         * 在HTML页面中支持超高清格式(HTML5)
   * 由Google公司推出的
     * <video>元素的属性
       * src - 引入视频文件的路径
       * autoplay - 自动播放视频
       * controls - 提供控制面板
       * loop - 表示循环播放
       * poster - 设置播放之前显示的图片
       * width和height - 设置显示视频的宽度和高度
       * preload - 预加载
         * auto - (默认值)自动加载
   * none - 不加载
   * metadata - 只加载视频的基本信息(不含视频)
     * 高级内容
       * 方法
         * play() - 播放视频
   * pause() - 暂停视频
   * load() - 加载视频
   * canPlayType() - 判断当前浏览器是否支持指定视频格式
       * 事件
         * play - 当视频播放时被触发
   * pause - 当视频暂停时被触发
   * ended - 当视频结束时被触发
   * error - 当视频错误时被触发
   * canplay - 不考虑整体情况下,只要能播放,就播放
   * canplaythrough - 考虑整体情况下,只要能播放,就播放
   * progress - 表示视频加载的进度
       * 属性 - 用于判断
         * paused - 表示判断当前视频是否暂停
     * 返回Boolean值,true表示暂停,false表示播放
   * ended - 表示判断当前视频是否播放完毕
     * 返回Boolean值,true表示完毕
   * duration - 表示当前视频的时长
   * currentTime - 表示当前视频播放的位置
   * 音频处理
     * <audio>元素
       * 第一种 - 只支持一种音频格式
         <audio src="音频文件的路径"></audio>
       * 第二种 - 同时引入多个音频格式
         <audio>
     <source src="一种音频格式" />
     <source src="一种音频格式" />
     <source src="一种音频格式" />
   </audio>
     * <audio>元素支持音频格式
       * MP3 - 目前最主流
       * OGG
       * WAV
 * Canvas(画布)
   * 基本内容
     * 简单来说,HTML5提供的新元素<canvas>
     * Canvas在HTML页面提供画布的功能
       * 在画布中绘制各种图形
     * Canvas绘制的图形与HTML页面无关
       * 无法通过DOM获取绘制的图形
       * 无法为绘制的图形绑定DOM事件
     * 只能使用Canvas提供的API
     * Canvas用途
       * 在HTML页面中绘制图表(例如柱状图、饼状图等)
       * 网页游戏 - Flash技术
         * 使用HTML5中的Canvas
   * 如何使用Canvas
     * 在HTML页面中定义<canvas>元素
     * 在javascript代码中
       * 获取<canvas>元素
       * 创建画布对象
         * getContext('2d')方法
       * 使用Canvas提供的API
   * 绘制图形
     * 绘制矩形
       * fillRect(x,y,width,height) - 实心矩形
         * x和y - 矩形的左上角坐标值
   * width - 设置矩形的宽度
   * height - 设置彗星的高度
       * strokeRect(x,y,width,height) - 空心矩形
       * clearRect(x,y,width,height)
         * 清除指定区域的矩形
     * 设置颜色
       * fillStyle - 设置填充颜色
       * strokeStyle - 设置描边颜色
       * globalAlpha - 设置透明度(0-1)
     * 设置渐变
       * 线型渐变 - createLinearGradient(x1,y1,x2,y2)
         * 具有基准线 - 起点(x1,y1)和终点(x2,y2)
       * 扇形(射线)渐变 - createRadialGradient(x1,y1,r1,x2,y2,r2)
         * 具有柱形(锥形) - 两个圆的面积
   * 参数
     * x1和y1 - 第一个圆的圆心坐标值
     * r1 - 第一个圆的半径
     * x2和y2 - 第二个圆的圆心坐标值
     * r2 - 第二个圆的半径
 * 扩展内容
   * Web前端 - 移动端
     * 移动智能终端
       * iPhone - IOS系统 - Object-c|Swfit
       * Android系统 - Java
       * Windows Mobile系统 - .net平台
       * BlackBerry系统 - 企业级应用 QNX
       * WebOS系统 - 全键盘+触摸屏
       * 塞班 - 诺基亚
       * MeeGo - Inter和诺基亚
     * 移动跨平台 - HTML|CSS|JAVASCRIPT
       * 一次编写,到处运行(phoneGap)
   * 游戏分类(画面)
     * 2D效果
     * 2.5D效果 - 实际还是2D技术,模拟3D效果
     * 3D效果
   * 作为前端Web开发人员的原则
     * 眼见为实 - 不适用我们前端人员
   * HTML5的难度
     * HTML5的核心API相对来讲,都不难
     * HTML5的案例真正难在逻辑(JS代码)
     * 总结 - HTML5离不开javascript
   * 回答疑问
     * 第二阶段的javascript,抓紧复习
       * 个人并不建议 - 留级
     * 编写简历 - 项目经验
       * 多做网上的案例
     * 建议买哪些书籍
       * 个人不建议任何书籍
   * 如何成为优秀的程序员
     * 自学能力很强
       * 网上的案例
       * 网上的资料
     * 善于归纳总结
     * 师傅领进门,修行在个人
   * 英文对于开发功能的影响
     * 英文 - 书面+口语
       * 口语 - 外企+合资
     * 计算机英文
       * class - 类|教室
       * bug - 错误|臭虫
       * ant - 版本|蚂蚁

HTML5 DAY03:
 * Canvas
   * 绘制图形
     * 绘制文字
       * 方法
         * fillText(text,x,y) - 实心文字
     * text - 绘制的文字内容
     * x和y - 绘制的坐标值
   * strokeText(text,x,y) - 空心文字
       * 属性
         * font - 类似于CSS中的font属性
   * textAlign - 设置文字的水平方向对齐
     * left - 左对齐
     * center - 水平居中
     * right - 右对齐
   * textBaseline - 设置文字的垂直方向对齐
     * top - 顶部对齐
     * middle - (垂直)居中对齐
     * bottom - 底部对齐
     * hanging - 悬挂基线
     * alphabetic - 字母基线
         * 注意
     * 无论是水平方向还是垂直方向对齐,基准线对齐,并不是文字对齐
     * 无论是水平方向还是垂直方向对齐,并不是必要的属性(不使用也是可以的)
     * 阴影效果
       * shadowColor - 设置阴影颜色
       * shadowOffsetX - 设置水平方向阴影
       * shadowOffsetY - 设置垂直方向阴影
       * shadowBlur - 设置阴影的模糊程度
     * 创建路径
       * (标识)方法
         * beginPath() - 表示开始创建路径
   * closePath() - 表示结束创建路径
       * 设置方法
         * rect(x,y,width,height) - 设置矩形形状
     * x和y - 设置矩形的左上角坐标值
     * width和height - 设置矩形的宽度和高度
   * arc(x,y,radius,startAngle,endAngle,direction) - 设置圆形形状
     * x和y - 设置圆形的圆心坐标值
     * radius - 设置圆形的半径
     * startAngle和endAngle - 设置圆形的起始位置
     * direction - 按照顺时针或逆时针绘制
       * 绘制方法
         * stroke() - 绘制轮廓
   * fill() - 绘制填充
     * 绘制线条(直线和折线、多边形) - 创建路径
       * moveTo(x,y) - 设置这条线的起点坐标值
       * lineTo(x,y) - 设置这条线的终点(折点)坐标值
   * 设置线条
     * lineWidth - 设置线条的宽度
       * 默认值为1(px)
     * lineCap - 设置线条端点的形状
       * butt - 默认值,平直
       * round - 圆角
       * square - 正方向
     * lineJoin - 设置两条线焦点的形状
       * miter - 默认值,尖角
       * round - 圆角
       * bevel - 斜角
     * miterLimit - 配合lineJoin使用
       * lineJoin设置为miter,该属性值设置尖角的延伸范围
 * Canvas处理图片
   * 绘制图片
     * drawImage(img,x,y) - 按照图片原大小加载
       * img - 当前加载(绘制)的图片
       * x和y - 绘制图片的坐标值(左上角)
     * drawImage(img,x,y,width,height) - 按照指定大小加载图片
       * img - 当前加载(绘制)的图片
       * x和y - 绘制图片的坐标值(左上角)
       * width和height - 设置绘制图片显示的宽度和高度
     * 注意
       * 必须保证图片加载完毕(onload事件)后,再绘制图片
   * 平铺图片
     * createPattern(img,type)
       * img - 平铺的图片
       * type - 平铺的方式
         * repeat - 平铺
   * no-repeat - 不平铺
   * repeat-x - 水平方向平铺
   * repeat-y - 垂直方向平铺
     * 注意
       * 必须保证图片加载完毕(onload事件)后,再绘制图片
   * 切割图片
     * clip() - 切割(按照创建路径使用)
   * 画布方法
     * scale(x,y) - 缩放(缩小或放大)
       * x - 表示水平方向的缩放
       * y - 表示垂直方向的缩放
       * 参数的取值
         * 如果为1的话,表示不缩放(原大小)
   * 如果小于1的话,表示缩小
   * 如果大于1的话,表示放大
     * translate(x,y) - 重新定位(x,y)
       * x和y - 新的坐标值
       * 注意 - x和y是相对于上次定位坐标值
     * rotate(旋转角度) - 旋转画布
       * 公式为 degrees * Math.PI / 180;
 * Chart.js - Canvas的JS库
   * 作用 - 提供各种图表
   * 如何使用
     * 在HTML页面中引入Chart.js文件
     * 在HTML页面中定义<canvas>元素
     * 在javascript代码中
       * 获取<canvas>元素
       * 创建画布对象
         var context = canvas.getContext("2d");
       * 通过画布对象,创建Chart对象
         var chart = new Chart(context);
       * 利用Chart对象调用API方法
         var data = [];
   chart.Pie(data);
   * 提供6种图表
     * 柱状图 - Bar(data,options)
     * 饼状图 - Pie(data,options)
     * 曲线图 - Line(data,options)
     * 环形图 - Doughnut(data,options)
     * 雷达图 - Radar(data,options)
     * 极地区域图 - PolarArea(data,options)
 * 作业
   * 位置、大小、颜色都随机的圆形
   * 将Chart.js其他4种图表实现一遍
 * 扩展内容
   * 前端Web开发时,建议使用以下几种浏览器
     * Chrome - 两个版本 - 版本更新过于频繁
       * 开发版本
         * 功能较新
   * 不稳定
       * 正式版本
         * 功能较旧
   * 稳定
       * Chrome OS
     * Firefox - 两个版本
       * 开发版本 - (开发)功能多
       * 正式版本
       * FireFox OS - 移动操作系统
         * 开发使用HTML|CSS|JAVASCRIPT
     * Safari
  * 内向问题
    * 面试 - 你认为你的性格,是外向还是内向?
      * 内向 - 沟通能力比较差,团队协作出问题
      * 外向 - 担心工作时,不够专心
    * 良好的沟通能力
      * 程序员 - 形成程序员思维
      * 都是学习和培养
  * Markdown编辑器
    * 支持Markdown文件的扩展名为".md"
  * 前面的内容忘记
    * 个人建议 - 在案例中复习


HTML5 DAY04:
 * SVG
   * 基本内容
     * SVG并不属于HTML5专有内容
       * HTML5提供有关SVG原生的内容
     * 在HTML5出现之前,就有SVG内容
     * SVG,简单来说就是矢量图
     * SVG文件的扩展名为".svg"
     * SVG使用的是XML语法
   * 概念
     * SVG是一种使用XML技术描述二维图形的语言
     * SVG的特点
       * SVG绘制图形可以被搜索引擎抓取
       * SVG在图片质量不下降的情况下,被放大
     * SVG与Canvas的区别
       * SVG
         * 不依赖分辨率
   * 支持事件绑定
   * 大型渲染区域的程序(例如百度地图)
   * 不能用来实现网页游戏
       * Canvas
         * 依赖分辨率
   * 不支持事件绑定
   * 最合适网页游戏
   * 保存为".jpg"格式的图片
     * 用途
       * 网页中一些小的图标
       * 网页中动态特效(动画效果)
   * HTML5中使用SVG
     * 使用<svg></svg>元素
       * 作用 - 类似于<canvas>元素
         * 默认大小为300px*150px
   * 使用CSS样式
     * 使用SVG绘制图形,必须定义<svg>元素中
   * 绘制图形
     * 矩形元素
       <rect x="" y="" width="" height="" />
     * 圆形元素
       <circle cx="" cy="" r="" />
     * 椭圆元素
       <ellipse cx="" cy="" rx="" ry="">
     * 直线元素
       <line x1="" y1="" x2="" y2="" />
     * 折线元素
       <polyline points="">
     * 多边形元素
       <polygon points="" />
   * 特效元素
     * 渐变 - 渐变元素定义在<defs>元素内
       * 线型渐变 - <linearGradient>
         * 该元素是起始元素
   <linearGradient x1="%" y1="%" x2="%" y2="%">
     <stop offset="%" stop-color="color" />
   </linearGradient>
       * 扇形(射线)渐变 - <radialGradient>
     * 滤镜 - 高斯模糊
       * 滤镜使用<filter>元素
       * <feGaussianBlur>元素 - 高斯模糊
         * in="SourceGraphic"
   * stdDeviation - 设置模糊程度
       * 注意 - 定义在<defs>元素中
 * TWO.js
   * 基本内容
     * JS库介绍
       * three.js - 专门用于绘制三维图形
       * two.js - 专门用于绘制二维图形
     * two.js支持的格式
       * SVG - 默认
       * Canvas
       * WebGL - 专门用于绘制图像
   * 如何使用two.js
     * 在HTML页面中引入two.js文件
     * 在HTML页面中定义容器(<div>)
     * 在javascript代码中
       * 获取HTML页面中的容器
       * 创建Two对象,将该对象添加到容器中
         new Two(params).appendTo(Element);
       * 使用two.js提供的API方法进行绘制
         * 利用two.js提供的方法,设置图形
   * 利用update()方法进行绘制
   * 创建Two对象
     * 构造器 - new Two(params)
     * params参数 - 设置当前对象的信息
       * type - 设置当前使用的格式(Two.Types.svg)
         * svg - 默认值
   * canvas
   * webgl
       * width和height - 设置宽度和高度
       * fullscreen - 设置是否全屏
         * Boolean值,true表示全屏
     * 图形方法
       * makeLine() - 绘制线条
       * makeRectangle() - 绘制矩形
       * makeCircle() - 绘制圆形
       * makeEllipse() - 绘制椭圆
     * 动画方法
       * update() - 更新动画
       * play() - 添加动画(循环)
       * pause() - 删除动画
   * 设置绘制图形的样式
     * 调用Two对象的绘制方法绘制图形时,返回该图形对象
     * 通过该图形对象,设置相关属性值
   * 分组操作
     * Two.Group
   * 动画效果
     * bind(event,callback)方法 - 事件绑定
       * event - 绑定事件名称
         * update - 对应update()方法的作用
   * 所有的DOM事件都可以绑定
       * callback - 事件处理函数
 * 扩展内容
   * 前端开发工具
     * Aptana Studio 3 - 代码提示
     * Webstrom - 国内前端开发人员神器
   * 实际开发中
     * 多用SVG
       * 不失真
       * 可被搜索
       * 页面优化 - 减少外部链接
         * <a href="">
   * <img src="">
     * Canvas - HTML绘制图形
       * 实际运行中,是以图片方式出现(.png)
         * 不能被搜索引擎抓取
   * 放大后失真
   * SVG内容
     * 内容量非常大
       * 静态绘制图形
       * 动态动画效果
       * 专门提供事件
     * 网上关于SVG的资料很少(没有书籍)
     * SVG的规范(W3C英文)
   * SVG或CANVAS在HTML页面中定义
     * 是只能定义一个元素,还是可以定义多个元素?
       * 在一个HTML页面可以定义多个<svg>或<canvas>元素
     * SVG还是CANVAS都是允许同时定义(绘制)多个图形
   * 在实际开发中的使用
     * SVG在将来的工作开发,使用率并不高
     * SVG图片一般都是由UI设计师来完成
     * SVG即使是我们自己来设计(绘制)
       * 目前网络上很多专门提供现成的SVG图片的网站
     * 使用JS库
   * 作业(思考)
     * 使用two.js实现圆形跟随鼠标移动的效果




HTML5 DAY05:
 * Geolocation(地理定位)
   * 基本内容
     * 地理定位 - 地球的经度和纬度的相交点
     * 实现地理定位的方式
       * GPS - 美国的,依靠卫星定位
       * 北斗定位 - 纯国产,惯性定位技术和卫星定位
       * 基站定位 - 移动运营商创建基站(提供信号源)
       * 基于互联网 - IP地址(PC端和移动端)
       * 目前很多浏览器都具有定位功能
   * HTML5中地理定位
     * 地理定位功能并不是属于HTML5专有内容
       * HTML5的地理定位技术,由Google公司提供的
       * Google Map产品
     * 中国 - 国内不能使用Google公司所有服务和产品
       * 百度地图和高德地图
   * 百度地图
     * 百度地图 - http://developer.baidu.com/map/
     * 注册百度开发者账户
       * http://developer.baidu.com/
     * 条件 - 必须能连接互联网
     * 目的 - 掌握如何使用百度地图
   * JS库或百度地图
     * 提供的API帮助文档
     * 提供的Demo示例代码
   * 学习目的
     * 学习的百度地图的功能
     * 百度地图的使用特点
   * 如何使用百度地图
     * 在HTML页面中
       * 引入百度地图的JS
         http://api.map.baidu.com/api?v=2.0&ak=秘钥
       * 定义显示地图的容器
         <div id="" style=""></div>
     * 在javascript代码中
       * 创建百度地图Map对象
         var map = new BMap.Map(容器id);
       * 进行地图的初始化
         map.centerAndZoom();
   * 百度地图的组件
     * 核心类 - Map类
       * 构造器 - BMap.Map(容器id);
       * 方法
         * centerAndZoom() - 初始化方法
   * addControl() - 添加控件
   * addOverlay() - 添加标注
     * Control类 - 控件类
       * ScaleControl类 - 表示地图的比例尺
         * 构造器 - 创建比例尺对象
       * NavigationControl类 - 表示移动缩放控件
         * 构造器 - 创建移动缩放控件
     * Overlay类 - 遮盖物类
       * Marker类 - 表示地图的一个标注
         * 构造器 - Marker(point)
     * Point类 - 标注类
 * 拖放(拖拽)API
   * 实现拖拽效果
     * 要拖拽的文件是什么? - 源元素
     * 要拖拽到哪里去? - 目标元素
   * 目前实现拖拽效果
     * 使用原生DOM就能实现 - 最麻烦
     * 使用jQuery的插件 - 拖拽效果
     * HTML5中提供的拖拽功能
   * HTML5中拖拽
     * 源元素事件
       * dragstart - 当鼠标开始拖放时被触发
       * drag - 当鼠标拖放过程中,类似于mousemove事件
       * dragend - 当鼠标结束拖放时被触发
     * 目标元素事件
       * dragenter - 当鼠标拖放进入到目标元素内被触发
       * dragover - 当鼠标到达目前元素被触发
         * 为该事件增加event.preventDefault();
       * drop - 当鼠标实现拖放效果时被触发
         * 默认情况下,该事件没有被触发
     * 原因 - HTML页面默认情况下,不允许拖放
       * 称之为HTML页面的默认行为
     * 解决 - 阻止页面的默认行为
       * 事件对象event.preventDefault()方法
       * dragleave - 当鼠标拖放离开目标元素被触发
     * dataTransfer对象
       * 作用 - 类似于window系统的剪切板的功能
       * 功能
         * 可以将源元素的信息(数据),存储在这里
   * 将存储在该对象的源元素信息,提供给目标元素
       * 方法
         * setData() - 设置(源元素)数据
     * 在源元素事件中使用
   * getData() - 获取设置的数据
     * 在目标元素事件中使用
   * clearData() - 清除(设置的)数据
     * 所有的数据内容,存储在浏览器内存中
     * 当使用完毕数据内容时,清除
     * setDragImage()方法
       * 作用 - 修改拖放过程中,鼠标跟随的图片效果
       * 用法 - drag、dragstart等事件
       * 注意 - 实际操作中,该方法几乎不用
 * 扩展内容
   * 建立自己的技术博客
     * 作用
       * 归纳学习技术知识和经验总结等
       * 帮助检查技术专业性或是否存在错误
       * 技术博客提供与别人交流平台
       * 面试时,公司会问是否拥有技术博客
     * 技术博客网站
       * CSDN - 技术圈知名度最大的
         http://blog.csdn.net/
       * 博客园 - 老牌的技术博客
         http://www.cnblogs.com/
       * iteye - 专注于技术博客
         http://www.iteye.com/blogs
       * 开发社区
         http://segmentfault.com/
   * 将作品放在网上可以访问(Web前端)
     * hexo - 使用nodejs编写的静态博客程序
       * 地址:https://hexo.io/
     * 搭建博客网站
       * github
         https://pages.github.com/
       * gitcafe
         https://gitcafe.com/
     * git软件的使用
















