# Canvas API
## 基本用法
  <canvas id="tutorial" width="150" height="150"></canvas>
  var canvas = document.getElementById('tutorial');
  var ctx = canvas.getContext('2d');
## 绘制形状
  ### 绘制矩形
  绘制一个填充的矩形: fillRect(x, y, width, height)
  绘制一个矩形的边框: strokeRect(x, y, width, height)
  清除指定矩形区域，让清除部分完全透明: clearRect(x, y, width, height)
  ### 绘制路径
  1. 首先，你需要创建路径起始点。
  2. 然后你使用画图命令去画出路径。
  3. 之后你把路径封闭。
  4. 一旦路径生成，你就能通过描边或填充路径区域来渲染图形。
  以下是所要用到的函数：
    beginPath()
    ·新建一条路径，生成之后，图形绘制命令被指向到路径上生成路径。
    closePath()
    ·闭合路径之后图形绘制命令又重新指向到上下文中。
    stroke()
    ·通过线条来绘制图形轮廓。
    fill()
    ·通过填充路径的内容区域生成实心的图形。
  ### 圆弧
  arc(x, y, radius, startAngle, endAngle, anticlockwise)
  ·画一个以（x,y）为圆心的以radius为半径的圆弧（圆），从startAngle开始到endAngle结束，按照anticlockwise给定的方向（默认为顺时针）来生成。
  ### 二次贝塞尔曲线及三次贝塞尔曲线
  quadraticCurveTo(cp1x, cp1y, x, y)
  ·绘制二次贝塞尔曲线，cp1x,cp1y为一个控制点，x,y为结束点。
  bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)
  ·绘制三次贝塞尔曲线，cp1x,cp1y为控制点一，cp2x,cp2y为控制点二，x,y为结束点。
  ### Path2D 对象
    new Path2D();     // 空的Path对象
    new Path2D(path); // 克隆Path对象
    new Path2D(d);    // 从SVG建立Path对象
## 添加样式和颜色
  fillStyle = color
  设置图形的填充颜色。
  strokeStyle = color
  设置图形轮廓的颜色。
  --透明度 Transparency
  --线型 Line styles
    lineWidth = value
    ·设置线条宽度。
    lineCap = type
    ·设置线条末端样式['butt','round','square']。
    lineJoin = type
    ·设定线条与线条间接合处的样式['round', 'bevel', 'miter']。
    miterLimit = value
    ·限制当两条线相交时交接处最大长度；所谓交接处长度（斜接长度）是指线条交接处内角顶点到外角顶点的长度。
    getLineDash()
    ·返回一个包含当前虚线样式，长度为非负偶数的数组。
    setLineDash(segments)
    ·设置当前虚线样式。
    lineDashOffset = value
    ·设置虚线样式的起始偏移量。
  --渐变 Gradients
    createLinearGradient(x1, y1, x2, y2)
    ·createLinearGradient 方法接受 4 个参数，表示渐变的起点 (x1,y1) 与终点 (x2,y2)。
    createRadialGradient(x1, y1, r1, x2, y2, r2)
    ·createRadialGradient 方法接受 6 个参数，前三个定义一个以 (x1,y1) 为原点，半径为 r1 的圆，后三个参数则定义另一个以 (x2,y2) 为原点，半径为 r2 的圆。
    gradient.addColorStop(position, color)
    ·addColorStop 方法接受 2 个参数，position 参数必须是一个 0.0 与 1.0 之间的数值，表示渐变中颜色所在的相对位置。例如，0.5 表示颜色会出现在正中间。color 参数必须是一个有效的 CSS 颜色值（如 #FFF， rgba(0,0,0,1)，等等）。
  --图案样式 Patterns
    createPattern(image, type)
    ·该方法接受两个参数。Image 可以是一个 Image 对象的引用，或者另一个 canvas 对象。Type 必须是下面的字符串值之一：repeat，repeat-x，repeat-y 和 no-repeat。
  --阴影 Shadows
    shadowOffsetX = float
    ·shadowOffsetX 和 shadowOffsetY 用来设定阴影在 X 和 Y 轴的延伸距离，它们是不受变换矩阵所影响的。负值表示阴影会往上或左延伸，正值则表示会往下或右延伸，它们默认都为 0。

    shadowOffsetY = float
    ·shadowOffsetX 和 shadowOffsetY 用来设定阴影在 X 和 Y 轴的延伸距离，它们是不受变换矩阵所影响的。负值表示阴影会往上或左延伸，正值则表示会往下或右延伸，它们默认都为 0。
    shadowBlur = float
    ·shadowBlur 用于设定阴影的模糊程度，其数值并不跟像素数量挂钩，也不受变换矩阵的影响，默认为 0。
    shadowColor = color
    ·shadowColor 是标准的 CSS 颜色值，用于设定阴影颜色效果，默认是全透明的黑色。
  --Canvas 填充规则
    "nonzero": non-zero winding rule, 默认值.
    "evenodd":  even-odd winding rule.
    eg.
      ctx.fill("evenodd");
## 绘制文本
  fillText(text, x, y [, maxWidth])
  ·在指定的(x,y)位置填充指定的文本，绘制的最大宽度是可选的.
  strokeText(text, x, y [, maxWidth])
  ·在指定的(x,y)位置绘制文本边框，绘制的最大宽度是可选的.
  --有样式的文本
    font = value
    ·当前我们用来绘制文本的样式. 这个字符串使用和 CSS font 属性相同的语法. 默认的字体是 10px sans-serif。
    textAlign = value
    ·文本对齐选项. 可选的值包括：start, end, left, right or center. 默认值是 start。
    textBaseline = value
    ·基线对齐选项. 可选的值包括：top, hanging, middle, alphabetic, ideographic, bottom。默认值是 alphabetic。
    direction = value
    ·文本方向。可能的值包括：ltr, rtl, inherit。默认值是 inherit。
  --预测量文本宽度
    measureText()
    ·将返回一个 TextMetrics对象的宽度、所在像素，这些体现文本特性的属性。
## 使用图片
  --引入图像到canvas里需要以下两步基本操作：
    获得一个指向HTMLImageElement的对象或者另一个canvas元素的引用作为源，也可以通过提供一个URL的方式来使用图片（参见例子）
    使用drawImage()函数将图片绘制到画布上
  --获得需要绘制的图片
    HTMLImageElement
    ·这些图片是由Image()函数构造出来的，或者任何的<img>元素
    HTMLVideoElement
    ·用一个HTML的 <video>元素作为你的图片源，可以从视频中抓取当前帧作为一个图像
    HTMLCanvasElement
    ·可以使用另一个 <canvas> 元素作为你的图片源。
    ImageBitmap
    ·这是一个高性能的位图，可以低延迟地绘制，它可以从上述的所有源以及其它几种源中生成。
    这些源统一由 CanvasImageSource类型来引用。
  --使用相同页面内的图片
    document.images集合
    document.getElementsByTagName()方法
    ·如果你知道你想使用的指定图片的ID，你可以用document.getElementById()获得这个图片
  --使用其它域名下的图片
    在 HTMLImageElement上使用crossOrigin属性，你可以请求加载其它域名上的图片
  --使用其它 canvas 元素
    和引用页面内的图片类似地，用 document.getElementsByTagName 或 document.getElementById 方法来获取其它 canvas 元素。
  --由零开始创建图像
    var img = new Image();   // 创建一个<img>元素
    img.src = 'myImage.png'; // 设置图片源地址
  --缩放 Scaling
  --切片 Slicing
  --控制图像的缩放行为 Controlling image scaling behavior
    ·Gecko 1.9.2 引入了 mozImageSmoothingEnabled 属性，值为 false 时，图像不会平滑地缩放。默认是 true 。
  
## 变形（Transformations）
  --状态的保存和恢复 Saving and restoring state
    save()
    ·保存画布(canvas)的所有状态
    restore()
    ·save 和 restore 方法是用来保存和恢复 canvas 状态的，都没有参数。Canvas 的状态就是当前画面应用的所有样式和变形的一个快照。
  --移动 Translating
    translate(x, y)
    ·translate 方法接受两个参数。x 是左右偏移量，y 是上下偏移量
  --旋转 Rotating
    rotate(angle)
    ·这个方法只接受一个参数：旋转的角度(angle)，它是顺时针方向的，以弧度为单位的值。
  --缩放 Scaling
    scale(x, y)
    ·scale  方法可以缩放画布的水平和垂直的单位。两个参数都是实数，可以为负数，x 为水平缩放因子，y 为垂直缩放因子，如果比1小，会比缩放图形， 如果比1大会放大图形。默认值为1， 为实际大小。
  --变形 Transforms
    transform(m11, m12, m21, m22, dx, dy)
  --resetTransform()
## 合成与剪裁
  --globalCompositeOperation
  --clip()
    ·将当前正在构建的路径转换为当前的裁剪路径。
## 动画
  ### 基本动画
  --动画的基本步骤
    1.清空 canvas
      ·除非接下来要画的内容会完全充满 canvas （例如背景图），否则你需要清空所有。最简单的做法就是用 clearRect 方法。
    2.保存 canvas 状态
      ·如果你要改变一些会改变 canvas 状态的设置（样式，变形之类的），又要在每画一帧之时都是原始状态的话，你需要先保存一下。
    3.绘制动画图形（animated shapes）
      ·这一步才是重绘动画帧。
    4.恢复 canvas 状态
      ·如果已经保存了 canvas 的状态，可以先恢复它，然后重绘下一帧。
  --操控动画 Controlling an animation
    ·可以通过 setInterval 和 setTimeout 方法来控制在设定的时间点上执行重绘。
  --有安排的更新画布 Scheduled updates
    -首先，可以用window.setInterval(), window.setTimeout(),和window.requestAnimationFrame()来设定定期执行一个指定函数。

    -setInterval(function, delay)
    ·当设定好间隔时间后，function会定期执行。
    -setTimeout(function, delay)
    ·在设定好的时间之后执行函数
 
    -requestAnimationFrame(callback)
    ·告诉浏览器你希望执行一个动画，并在重绘之前，请求浏览器执行一个特定的函数来更新动画。
  ### 高级动画
## 像素操作
  --ImageData 对象
    -创建一个ImageData对象
      var myImageData = ctx.createImageData(width, height);
      var myImageData = ctx.createImageData(anotherImageData);
  --得到场景像素数据
    var myImageData = ctx.getImageData(left, top, width, height);
  --颜色选择器
  --在场景中写入像素数据
    ctx.putImageData(myImageData, dx, dy);
  --图片灰度和反相颜色
  --保存图片
    canvas.toDataURL('image/png')
    ·默认设定。创建一个PNG图片。
    canvas.toDataURL('image/jpeg', quality)
    ·创建一个JPG图片。你可以有选择地提供从0到1的品质量，1表示最好品质，0基本不被辨析但有比较小的文件大小。
    canvas.toBlob(callback, type, encoderOptions)
    ·这个创建了一个在画布中的代表图片的Blob对像。
## 点击区域和无障碍访问
  --点击区域（hit region）
    CanvasRenderingContext2D.addHitRegion() 
    ·在canvas上添加一个点击区域。
    CanvasRenderingContext2D.removeHitRegion() 
    ·从canvas上移除指定id的点击区域。
    CanvasRenderingContext2D.clearHitRegions() 
    ·移除canvas上的所有点击区域。
    **你可以把一个点击区域添加到路径里并检测MouseEvent.region属性来测试你的鼠标有没有点击这个区域
  --焦点圈
    CanvasRenderingContext2D.drawFocusIfNeeded() 
    ·如果给定的元素获得了焦点，这个方法会沿着在当前的路径画个焦点圈。
    CanvasRenderingContext2D.scrollPathIntoView() 
    ·把当前的路径或者一个给定的路径滚动到显示区域内。
## canvas的优化
  1. 在离屏canvas上预渲染相似的图形或重复的对象
  2. 避免浮点数的坐标点，用整数取而代之
  3. 不要在用drawImage时缩放图像
  4. 使用多层画布去画一个复杂的场景
  5. 用CSS设置大的背景图
  6. 用CSS transforms特性缩放画布
  7. 关闭透明度
  8. 将画布的函数调用集合到一起（例如，画一条折线，而不要画多条分开的直线）
  9. 避免不必要的画布状态改变
  10. 渲染画布中的不同点，而非整个新状态
  11. 尽可能避免 shadowBlur特性
  12. 尽可能避免text rendering
  13. 使用不同的办法去清除画布(clearRect() vs. fillRect() vs. 调整canvas大小)
  14. 有动画，请使用window.requestAnimationFrame() 而非window.setInterval()
  请谨慎使用大型物理库
## 其他的Web APIs
  --WebGL
  ·用于渲染交互式3D图形的API.
  --SVG
  ·可缩放矢量图形（简称SVG）允许你使用矢量线，矢量图形，确保无论图片大小都可以比例平滑地显示.
  --Web Audio
  ·Web Audio API提供了Web上的音频控制——个强大和灵活的系统，允许开发人员选择的音频源，添加效果的音频，创建音频可视化，应用空间效应（如平移）等等。