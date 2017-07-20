# jquery 面试题

标签（空格分隔）： 面试题 前端 找工作

---
https://www.oschina.net/translate/jquery-interview-questions-answers-programmers
### 1. jQuery 库中的 $() 是什么？（答案如下）

$() 函数是 jQuery() 函数的别称，乍一看这很怪异，还使 jQuery 代码晦涩难懂。一旦你适应了，你会爱上它的简洁。$() 函数用于将任何对象包裹成 jQuery 对象，接着你就被允许调用定义在 jQuery 对象上的多个不同方法。你甚至可以将一个选择器字符串传入 $() 函数，它会返回一个包含所有匹配的 DOM 元素数组的 jQuery 对象。这个问题我已经见过好几次被提及，尽管它非常基础，它经常被用来区分一个开发人员是否了解 jQuery。

### 2. 网页上有 5 个 <div> 元素，如何使用 jQuery来选择它们？（答案）

另一个重要的 jQuery 问题是基于选择器的。jQuery 支持不同类型的选择器，例如 ID 选择器、class 选择器、标签选择器。鉴于这个问题没提到 ID 和 class，你可以用标签选择器来选择所有的 div 元素。jQuery 代码：$("div")，这样会返回一个包含所有 5 个 div 标签的 jQuery 对象。更详细的解答参见上面链接的文章。

### 3. jQuery 里的 ID 选择器和 class 选择器有何不同？（答案）

如果你用过 CSS，你也许就知道 ID 选择器和 class 选择器之间的差异，jQuery 也同样如此。ID 选择器使用 ID 来选择元素，比如 #element1，而 class 选择器使用 CSS class 来选择元素。当你只需要选择一个元素时，使用 ID 选择器，而如果你想要选择一组具有相同 CSS class 的元素，就要用 class 选择器。在面试过程中，你有很大几率会被要求使用 ID 选择器和 class 选择器来写代码。下面的 jQuery 代码使用了 ID 选择器和 class 选择器：
```
$('#LoginTextBox')  // Returns element wrapped as jQuery object with id='LoginTextBox'
$('.active') // Returns all elements with CSS class active.
```
正如你所见，从语法角度来说，ID 选择器和 class 选择器的另一个不同之处是，前者用字符”#”而后者用字符”.”。更详细的分析和讨论参见上面的答案链接。

### 4. 如何在点击一个按钮时使用 jQuery 隐藏一个图片？

这是一个事件处理问题。jQuery为按钮点击之类的事件提供了很好的支持。你可以通过以下代码去隐藏一个通过ID或class定位到的图片。你需要知道如何为按钮设置事件并执行hide() 方法，代码如下所示：
```
$('#ButtonToClick').click(function(){
    $('#ImageToHide').hide();
});
```
我喜欢这个问题，因为很贴近实际使用，代码也不复杂。

### 5.  $(document).ready() 是个什么函数？为什么要用它？(answer)

这个问题很重要，并且常常被问到。 ready() 函数用于在文档进入ready状态时执行代码。当DOM 完全加载（例如HTML被完全解析DOM树构建完成时），jQuery允许你执行代码。使用$(document).ready()的最大好处在于它适用于所有浏览器，jQuery帮你解决了跨浏览器的难题。需要进一步了解的用户可以点击 answer链接查看详细讨论。

### 6. JavaScript window.onload 事件和 jQuery ready 函数有何不同？（答案）

这个问答是紧接着上一个的。JavaScript window.onload 事件和 jQuery ready 函数之间的主要区别是，前者除了要等待 DOM 被创建还要等到包括大型图片、音频、视频在内的所有外部资源都完全加载。如果加载图片和媒体内容花费了大量时间，用户就会感受到定义在 window.onload 事件上的代码在执行时有明显的延迟。

另一方面，jQuery ready() 函数只需对 DOM 树的等待，而无需对图像或外部资源加载的等待，从而执行起来更快。使用 jQuery $(document).ready() 的另一个优势是你可以在网页里多次使用它，浏览器会按它们在 HTML 页面里出现的顺序执行它们，相反对于 onload 技术而言，只能在单一函数里使用。鉴于这个好处，用 jQuery ready() 函数比用 JavaScript window.onload 事件要更好些。

### 7. 如何找到所有 HTML select 标签的选中项？（答案如下）

这是面试里比较棘手的 jQuery 问题之一。这是个基础的问题，但是别期望每个 jQuery 初学者都知道它。你能用下面的 jQuery 选择器获取所有具备 multiple=true 的 <select > 标签的选中项：

$('[name=NameOfSelectedTag] :selected')
这段代码结合使用了属性选择器和 :selected 选择器，结果只返回被选中的选项。你可按需修改它，比如用 id 属性而不是 name 属性来获取 <select> 标签。

### 8. jQuery 里的 each() 是什么函数？你是如何使用它的？（答案如下）

each() 函数就像是 Java 里的一个 Iterator，它允许你遍历一个元素集合。你可以传一个函数给 each() 方法，被调用的 jQuery 对象会在其每个元素上执行传入的函数。有时这个问题会紧接着上面一个问题，举个例子，如何在 alert 框里显示所有选中项。我们可以用上面的选择器代码找出所有选中项，然后我们在 alert 框中用 each() 方法来一个个打印它们，代码如下：
```
$('[name=NameOfSelectedTag] :selected').each(function(selected) {
    alert($(selected).text());
});
```
其中 text() 方法返回选项的文本。

### 9. 你是如何将一个 HTML 元素添加到 DOM 树中的？（答案如下）

你可以用 jQuery 方法 appendTo() 将一个 HTML 元素添加到 DOM 树中。这是 jQuery 提供的众多操控 DOM 的方法中的一个。你可以通过 appendTo() 方法在指定的 DOM 元素末尾添加一个现存的元素或者一个新的 HTML 元素。

### 10. 你能用 jQuery 代码选择所有在段落内部的超链接吗？（答案略）

这是另一个关于选择器的 jQuery 面试题。就像其他问题那样，只需一行 jQuery 代码就能搞定。你可以使用下面这个 jQuery 代码片段来选择所有嵌套在段落（<p>标签）内部的超链接（<a>标签）……

### 11. $(this) 和 this 关键字在 jQuery 中有何不同？（答案如下）

这对于很多 jQuery 初学者来说是一个棘手的问题，其实是个简单的问题。$(this) 返回一个 jQuery 对象，你可以对它调用多个 jQuery 方法，比如用 text() 获取文本，用val() 获取值等等。而 this 代表当前元素，它是 JavaScript 关键词中的一个，表示上下文中的当前 DOM 元素。你不能对它调用 jQuery 方法，直到它被 $() 函数包裹，例如 $(this)。




---
http://www.jianshu.com/p/dd76ee437a60

1 你在公司是怎么用jquery的？

答：在项目中是怎么用的是看看你有没有项目经验(根据自己的实际情况来回答) 你用过的选择器啊，复选框啊，表单啊，ajax啊，事件等
配置jQuery环境 下载jquery类库 在jsp页面引用jquery类库即可

<script type="text/[JavaScript](http://lib.csdn.net/base/javascript)" src="jquery/jquery-1.7.2.min.js"/>
接下来通过在<script> $(function(){ }); </script>

2 你为什么要使用jquery？

答：因为jQuery是轻量级的框架，大小不到30kb,它有强大的选择器，出色的DOM操作的封装，有可靠的事件处理机制(jQuery在处理事件绑定的时候相当的可靠)，完善的ajax(它的ajax封装的非常的好，不需要考虑复杂浏览器的兼容性和XMLHttpRequest对象的创建和使用的问题。) 出色的浏览器的兼容性。 而且支持链式操作，隐式迭代。行为层和结构层的分离，还支持丰富的插件，jquery的文档也非常的丰富。

3 你觉得jquery有哪些好处？ 答案同上

4 你使用jquery遇到过哪些问题，你是怎么解决的？

答：这个答案是开发的，看你是否有相关的项目经验。
例前台拿不到值，JSON 可是出现的错误(多了一个空格等)这编译是不会报错的 jquery库与其他库冲突：
1>如果其他库在jquery库之前导入的话
1.我们可以通过jquery.noconflict()将变量的$的控制权过度给其他库
2.自定义快捷键,用一个变量接住jquery.noconflict()
3.通过函数传参
2>如果jquery库在其他库之前导入就直接使用jquery
今天在处理一个数据问题时，发现jQuery.ajax()方法返回的值一直有问题，清除缓存后数据无误，多次测试后发现返回的值都是之前的值，并且一直未执行url(后台为Java，设置断点一直未进入)。在网上查找下,发现是未设置type的原因。 如果没设置jQuery.ajax的type="Post"，那么ajax就会默认type="Get"，这就会导致之前数据被缓存起来。加上type="Post"，问题解决！

5 你知道jquery中的选择器吗，请讲一下有哪些选择器？

答 ：jQuery中的选择器大致分为:基本选择器，层次选择器，过滤选择器，表单选择器

6 jquery中的选择器 和 css中的选择器有区别吗？

答：jQuery选择器支持CSS里的选择器，jQuery选择器可用来添加样式和添加相应的行为CSS 中的选择器是只能添加相应的样式

7 你觉得jquery中的选择器有什么优势？

答：简单的写法 $('ID') 来代替 document.getElementById()函数
支持CSS1 到CSS3 选择器完善的处理机制(就算写错了id也不会报错)

8 你在使用选择器的时候有有没有什么觉得要注意的地方？

答: 1 选择器中含有".","#","[" 等特殊字符的时候需要进行转译
2 属性选择器的引号问题
3 选择器中含有空格的注意事项

9 jquery对象和dom对象是怎样转换的？

答 ：jquery转DOM对象:jQuery 对象是一个数组对象，可以通过[index]的丰富得到相应的DOM对象还可以通过get[index]去得到相应的DOM对象。DOM对象转jQuery对象:$(DOM对象)

10 你是如何使用jquery中的ajax的？

答: 如果是一些常规的ajax程序的话，使用load(),$.get(),$.post(),就可以搞定了，一般我会使用的是$.post() 方法。如果需要设定beforeSend(提交前回调函数),error(失败后处理),success(成功后处理)及complete(请求完成后处理)回调函数等，这个时候我会使用$.ajax()

11 你觉得jquery中的ajax好用吗，为什么？

答: 好用的。 因为jQuery提供了一些日常开发中夙瑶的快捷操作，例 load，ajax，get，post等等，所以使用jQuery开发ajax将变得极其简单，我们就可以集中精力在业务和用户的体验上，不需要去理会那些繁琐的XMLHttpRequest对象了。

12 jquery中$.get()提交和$.post()提交有区别吗？

答: 1 $.get() 方法使用GET方法来进行异步请求的。$.post() 方法使用POST方法来进行异步请求的。
2 get请求会将参数跟在URL后进行传递，而POST请求则是作为HTTP消息的实体内容发送给Web服务器的，这种传递是对用户不可见的。
3 get方式传输的数据大小不能超过2KB 而POST要大的多
4 GET 方式请求的数据会被浏览器缓存起来，因此有安全问题。

13 jquery中的load方法一般怎么用的？

答：load方法一般在 载入远程HTML 代码并插入到DOM中的时候用，通常用来从Web服务器上获取静态的数据文件。如果要传递参数的话，可以使用$.get() 或 $.post()。

14 在jquery中你是如何去操作样式的？

答: addClass() 来追加样式 ，removeClass() 来删除样式，toggle() 来切换样式

15 简单的讲叙一下jquery是怎么处理事件的，你用过哪些事件？

答: 首先去装载文档，在页面家在完毕后，浏览器会通过javascript 为DOM元素添加事件。

16 你使用过jquery中的动画吗，是怎样用的？

答:使用过。
hide() 和 show() 同时修改多个样式属性。像高度，宽度，不透明度。 fadeIn() 和fadeOut() fadeTo() 只改变不透明度
slideUp() 和 slideDown() slideToggle() 只改变高度
animate() 属于自定义动画的方法.

17 你使用过jquery中的插件吗？ 答:看个人的实力和经验来回答了。

18 你一般用什么去提交数据，为什么？

答:一般我会使用的是$.post() 方法。
如果需要设定beforeSend(提交前回调函数),error(失败后处理),success(成功后处理及complete(请求完成后处理)回调函数等，这个时候我会使用$.ajax()

19 在jquery中引入css有几种方式？

答:四种 行内式，内嵌式，导入式，链接式

20 你在jquery中使用过哪些插入节点的方法，它们的区别是什么？

答:append(),appendTo(),prepend(),prependTo(),after(),insertAfter()，before(),insertBefore() 大致可以分为 内部追加和外部追加append() 表式向每个元素内部追加内容。appendTo()表示 讲所有的元素追加到指定的元素中。例$(A)appendTo(B) 是将A追加到B中下面的方法解释类似。

21 你使用过包裹节点的方法吗，包裹节点有方法有什么好处？

答: wrapAll(),wrap(), wrapInner() 需要在文档中插入额外的结构化标记的时候可以使用这些包裹的方法应为它不会帛画原始文档的语义

22 jquery中如何来获取或和设置属性？

jQuery中可以用attr()方法来获取和设置元素属性removeAttr() 方法来删除元素属性

23 如何来设置和获取HTML 和文本的值？

答：html()方法 类似于innerHTML属性 可以用来读取或者设置某个元素中的HTML内容
注意：html() 可以用于xhtml文档 不能用于xml文档text() 类似于innerText属性 可以用来读取或设置某个元素中文本内容。val() 可以用来设置和获取元素的值

24 你jquery中有哪些方法可以遍历节点？

答 ：children() 取得匹配元素的子元素集合,只考虑子元素不考虑后代元素 next() 取得匹配元素后面紧邻的同辈元素
prev() 取得匹配元素前面紧邻的同辈元素
siblings() 取得匹配元素前后的所有同辈元素
closest() 取得最近的匹配元素
find() 取得匹配元素中的元素集合 包括子代和后代

25 子元素选择器 和后代选择器元素有什么区别？

答:子代元素是找子节点下的所有元素,后代元素是找子节点或子节点的子节点中的元素

26 在jquery中可以替换节点吗？

答：可以 在jQuery中有两者替换节点的方式 replaceWith() 和 replaceAll()例如在<p title="hao are you">hao are you</p>替换成I am fine$('p').replaceWith('I am fine'); replaceAll 与replaceWith的用法前后调换一下即可。

27 你觉得beforeSend方法有什么用？

答：发送请求前可以修改XMLHttpRequest对象的函数，在beforeSend中如果返回false 可以取消本次的Ajax请求。XMLHttpRequest对象是唯一的参数所以在这个方法里可以做验证

28 siblings() 方法 和 $('prev~div')选择器是一样的嘛？

答: $('prev~div') 只能选择'#prev'元素后面的同辈<div>元素而siblings()方法与前后的文职无关，只要是同辈节点就都能匹配。

29 你在ajax中使用过JSON吗，你是如何用的？

答:使用过，在$.getJSON() 方法的时候就是。
因为 $.getJSON() 就是用于加载JSON文件的

30 有哪些查询节点的选择器？

答：我在公司使用过 :first 查询第一个，:last 查询最后一个，:odd查询奇数但是索引从0开始:even 查询偶数，:eq(index)查询相等的 ,:gt(index)查询大于index的 ,:lt查询小于index:header 选取所有的标题等

31 nextAll() 能 替代$('prev~siblindgs')选择器吗？

答:能。 使用nextAll() 和使用$('prev~siblindgs') 是一样的

32 jQuery中有几种方法可以来设置和获取样式

答 ：addClass() 方法，attr() 方法

33 $(document).ready()方法和window.onload有什么区别？

答: 两个方法有相似的功能，但是在实行时机方面是有区别的。 1window.onload方法是在网页中所有的元素(包括元素的所有关联文件)完全加载到浏览器后才执行的。
2 $(document).ready() 方法可以在DOM载入就绪时就对其进行操纵，并调用执行绑定的函数。

34 jQuery是如何处理缓存的？

答 ：要处理缓存就是禁用缓存.
1 通过$.post() 方法来获取数据，那么默认就是禁用缓存的。
2 通过$.get()方法 来获取数据，可以通过设置时间戳来避免缓存。可以在URL后面加上+(+new Date)例 $.get('ajax.xml?'+(+new Date),function () { //内容 }); 3 通过$.ajax 方法来获取数据，只要设置cache:false即可。

35 $.getScript()方法 和 $.getJson() 方法有什么区别？

答: 1 $.getScript() 方法可以直接加载.js文件，并且不需要对javascript文件进行处理，javascript文件会自动执行。
2 $.getJson() 是用于加载JSON 文件的 ，用法和$.getScript()

36 你读过有关于jQuery的书吗？

《jquery基础教程》 《jquery实战》《锋利的jquery》 《巧用jquery》 《jQuery用户界面库学习指南》等

37 $("#msg").text(); 和 $("#msg").text("new content");有什么区别？

答：1 $("#msg").text() 是 返回id为msg的元素节点的文本内容
2 $("#msg").text("new content"); 是 将“new content” 作为普通文本串写入id为msg的元素节点内容中, 页面显示粗体的new content

38 radio单选组的第二个元素为当前选中值，该怎么去取？

答 : $('input[name=items]').get(1).checked = true;

39 选择器中 id，class有什么区别？

答：在网页中 每个id名称只能用一次，class可以允许重复使用

40 你使用过哪些数据格式，它们各有什么特点？

答: HTML格式 ,JSON格式,javascript格式,XML格式
1 HTML片段提供外部数据一般来说是最简单的。
2 如果数据需要重用，而且其他应用程序也可能一次受到影响，那么在性能和文件大小方面具有优势的JSON通常是不错的选择。
3 而当远程应用程序未知时，XML则能够为良好的互操作性提供最可靠的保证。

41 jQuery 能做什么？

答：1 获取页面的元素
2 修改页面的外观
3 改变页面大的内容
4 响应用户的页面操作
5 为页面添加动态效果
6 无需刷新页面，即可以从服务器获取信息
7 简化常见的javascript任务

42 在ajax中data主要有几种方式？

答 ： 三种，html拼接的，json数组，form表单经serialize()序列化的。

43 ：jQuery中的hover()和toggle()有什么区别？

答 hover()和toggle()都是jQuery中两个合成事件。
hover()方法用于模拟光标悬停事件。 toggle()方法是连续点击事件。

44 你知道jQuery中的事件冒泡吗，它是怎么执行的，何如来停止冒泡事件？

答 : 知道,事件冒泡是从里面的往外面开始触发。在jQuery中提供了stopPropagation()方法可以停止冒泡。

45 例如 单击超链接后会自动跳转，单击"提交"按钮后表单会提交等，有时候我想阻止这些默认的行为，该怎么办？

答: 可以用 event.preventDefault()或在事件处理函数中返回false，即 return false;

46.jquery表单提交前有几种校验方法？分别为？？

a) formData:返回一个数组，可以通过循环调用来校验
b) jaForm：返回一个jQuery对象，所有需要先转换成dom对象
c) fieldValue：返回一个数组beforeSend()

47.在jquery中你有没有编写过插件，插件有什么好处？你编写过那些插件？它应该注意那些？

a) 答: 插件的好处：对已有的一系列方法或函数的封装，以便在其他地方重新利用，方便后期维护和提高开发效率插件的分类：封装对象方法插件 、封装全局函数插件、选择器插件
b) 注意的地方：
i. 1.插件的文件名推荐命名为jquery.[插件名].js，以免和其他的javaScript库插件混淆
ii. 2.所有的对象方法都应当附加到jQuery.fn对象上，而所有的全局函数都应当附加到jQuery对象本身上
iii. 3.插件应该返回一个jQuery对象，以保证插件的可链式操作
iv. 4.避免在插件内部使用$作为jQuery对象的别名,而应使用完整的jQuery来表示，这样可以避免冲突或使用闭包来避免
v. 5.所有的方法或函数插件，都应当一分好结尾，否则压缩的时候可能出现问题。在插件头部加上分号，这样可以避免他人的不规范代码给插件带来影响
vi. 6.在插件中通过$.extent({})封装全局函数,选择器插件，扩展已有的object对象通过$.fn.extend({})封装对象方法插件

作者：山豆山豆
链接：http://www.jianshu.com/p/dd76ee437a60
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



---
http://www.codeceo.com/article/jquery-interview.html
### 问题：jQuery中有哪几种类型的选择器？

回答：从我自己的角度来讲，可以有3种类型的选择器，如下：

1、基本选择器：直接根据id、css类名、元素名返回匹配的dom元素。

2、层次选择器：也叫做路径选择器，可以根据路径层次来选择相应的DOM元素。

3、过滤选择器：在前面的基础上过滤相关条件，得到匹配的dom元素。

### 问题：请使用jQuery将页面上的所有元素边框设置为2px宽的虚线？

回答：这正是jQuery选择器上场的时候了，代码如下：
```
<script language="javascript" type="text/javascript">

         $("*").css("border", "2px dotted red"); 

</script>
```
### 问题：当CDN上的jQuery文件不可用时，该怎么办？

回答：为了节省带宽和脚本引用的稳定性，我们会使用CDN上的jQuery文件，例如google的jquery cdn服务。但是如果这些CDN上的jQuery服务不可用，我们还可以通过以下代码来切换到本地服务器的jQuery版本：
```
<script type="text/javascript" language="Javascript" src="http://ajax.aspnetcdn.com/ajax/jquery/jquery-1.4.1.min.js "></script>

<script type='text/javascript'>//<![CDATA[

if (typeof jQuery == 'undefined') {

document.write(unescape("%3Cscript src='/Script/jquery-1.4.1.min.js' type='text/javascript' %3E%3C/script%3E"));

}//]]>

</script>
```
### 问题：如何使用jQuery实现点击按钮弹出一个对话框？

回答：代码如下：

HTML：
```
<input id="inputField" type="text" size="12"/>
```
jQuery：
```
<script type="text/javascript"> $(document).ready(function () { $('#Button1').click(function () { alert($('#inputField').attr("value")); }); }); </script>
```
### 问题：jQuery中的Delegate()函数有什么作用？

回答：delegate()会在以下两个情况下使用到：

1、如果你有一个父元素，需要给其下的子元素添加事件，这时你可以使用delegate()了，代码如下：
```
$("ul").delegate("li", "click", function(){

$(this).hide();

});
```
2、当元素在当前页面中不可用时，可以使用delegate()

### 问题：怎样用jQuery编码和解码URL？

回答：在jQuery中，我们可以使用以下方法实现URL的编码和解码。
```
encodeURIComponent(url) and decodeURIComponent(url)
```
### 问题：如何用jQuery禁用浏览器的前进后退按钮？

回答：实现代码如下：
```
<script type="text/javascript" language="javascript">

$(document).ready(function() {

     window.history.forward(1);

     //OR

     window.history.forward(-1);

});

</script>
```

