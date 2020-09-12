# Game.map.visual

地图可视化（Map visual）提供了一种途径来在游戏地图上显示各种可视化的调试信息。您可以使用 `Game.map.visual` 对象来绘制一些仅对您可见的简单图形。

地图可视化不会被存储在游戏数据库中，它们唯一的作用就是在您的浏览器上显示一些信息。所有的绘制效果只会被保留一个 tick，并且如果下个 tick 没有更新的话它们就会消失。所有的 `Game.map.visual` 调用都不会产生 CPU 消耗（只会产生一些代码执行的自然成本，并且大多与简单的 `JSON.serialize` 调用有关）。然而，这里有一条使用限制：您最多只能为每个房间发布 1000 KB 的序列化数据。

所有绘制坐标均等同于全局游戏坐标 ([`RoomPosition`](#RoomPosition))。


{% api_method line 'pos1, pos2, [style]' 0 %}

```javascript
Game.map.visual.line(creep.pos, target.pos,
    {color: '#ff0000', lineStyle: 'dashed'});
```

绘制一条线。

{% api_method_params %}
pos1 : <a href="#RoomPosition">RoomPosition</a>
起始点位置对象。
===
pos2 : <a href="#RoomPosition">RoomPosition</a>
结束点位置对象。
===
style (可选) : object
包含下列属性的对象：
<ul>
    <li>
        <div class="api-arg-title">width</div>
        <div class="api-arg-type">number</div>
        <div class="api-arg-desc">线条的宽度，默认值为 0.1。</div>
    </li>
    <li>
        <div class="api-arg-title">color</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc">线条颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 <code>#ffffff<code>。</div>
    </li>
    <li>
        <div class="api-arg-title">opacity</div>
        <div class="api-arg-type">number</div>
        <div class="api-arg-desc">透明度，默认值为 0.5。</div>
    </li>
    <li>
        <div class="api-arg-title">lineStyle</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc"><code>undefined</code> (实线)，<code>dashed</code> (虚线) 或者 <code>dotted</code> (点线) 之一。默认值为 undefined。</div>
    </li>
</ul>
				
{% endapi_method_params %}


### 返回值

<code>MapVisual</code> 对象本身，以便进行链式调用。


{% api_method circle 'pos, [style]' 0 %}

```javascript
Game.map.visual.circle(new RoomPosition(25,25,'E2S7'));
```

```javascript
Game.map.visual.circle(nuker.pos, {fill: 'transparent', radius: NUKE_RANGE*50, stroke: '#ff0000'});
```

绘制一个圆。

{% api_method_params %}
pos : <a href="#RoomPosition">RoomPosition</a>
中心点位置对象。
===
style (可选) : object
包含下列属性的对象：
<ul>
    <li>
        <div class="api-arg-title">radius</div>
        <div class="api-arg-type">number</div>
        <div class="api-arg-desc">圆的半径，默认值为 10。</div>
    </li>
    <li>
        <div class="api-arg-title">fill</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc">线条颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 <code>#ffffff<code>。</div>
    </li>
    <li>
        <div class="api-arg-title">opacity</div>
        <div class="api-arg-type">number</div>
        <div class="api-arg-desc">透明度，默认值为 0.5。</div>
    </li>
    <li>
        <div class="api-arg-title">stroke</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc">轮廓颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 undefined（无轮廓）。</div>
    </li>
    <li>
        <div class="api-arg-title">strokeWidth</div>
        <div class="api-arg-type">number</div>
        <div class="api-arg-desc">轮廓宽度，默认值为 0.5。</div>
    </li>
    <li>
        <div class="api-arg-title">lineStyle</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc"><code>undefined</code> (实线)，<code>dashed</code> (虚线) 或者 <code>dotted</code> (点线) 之一。默认值为 undefined。</div>
    </li>
</ul>
				
{% endapi_method_params %}


### 返回值

<code>MapVisual</code> 对象本身，以便进行链式调用。


{% api_method rect 'topLeftPos, width, height, [style]' 0 %}

```javascript
// tower 的最佳效果区域
Game.map.visual.rect(new RoomPosition(tower.pos.x - 5, tower.pos.y - 5, tower.pos.roomName), 
    11, 11,
    {fill: 'transparent', stroke: '#ff0000'});
```

绘制一个矩形。

{% api_method_params %}
topLeftPos : <a href="#RoomPosition">RoomPosition</a>
左上角的位置对象。
===
width : number
矩形的宽。
===
height : number
矩形的高。
===
style (可选) : object
包含下列属性的对象：
<ul>
    <li>
        <div class="api-arg-title">fill</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc">线条颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 <code>#ffffff<code>。</div>
    </li>
    <li>
        <div class="api-arg-title">opacity</div>
        <div class="api-arg-type">number</div>
        <div class="api-arg-desc">透明度，默认值为 0.5。</div>
    </li>
    <li>
        <div class="api-arg-title">stroke</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc">轮廓颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 undefined（无轮廓）。</div>
    </li>
    <li>
        <div class="api-arg-title">strokeWidth</div>
        <div class="api-arg-type">number</div>
        <div class="api-arg-desc">轮廓宽度，默认值为 0.5。</div>
    </li>
    <li>
        <div class="api-arg-title">lineStyle</div>
        <div class="api-arg-type">string</div>
        <div class="api-arg-desc"><code>undefined</code> (实线)，<code>dashed</code> (虚线) 或者 <code>dotted</code> (点线) 之一。默认值为 undefined。</div>
    </li>
</ul>
				
{% endapi_method_params %}


### 返回值

<code>MapVisual</code> 对象本身，以便进行链式调用。


{% api_method poly 'points, [style]' 0 %}

```javascript
const points = [];
points.push(creep1.pos);
points.push(Game.rooms.E2S7.storage.pos);
points.push(new RoomPosition(20,21,'W1N1'));
Game.map.visual.poly(points, {fill: 'aqua'}); 
```

```javascript
// 将路径可视化
const path = PathFinder.search(creep.pos, creep.room.storage.pos).path;
Game.map.visual.poly(path, {stroke: '#ffffff', strokeWidth: .8, opacity: .2, lineStyle: 'dashed'});
```

绘制一段折线.

{% api_method_params %}
points : array
包含了所有拐点的数组。每个数组元素都应是一个 <a href="#RoomPosition"><code>RoomPosition</code></a> 对象。
===
style (可选) : object
包含下列属性的对象：
					<ul>
						<li>
							<div class="api-arg-title">fill</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">填充颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 <code>undefined</code>（无填充）。</div>
						</li>
						<li>
							<div class="api-arg-title">opacity</div>
							<div class="api-arg-type">number</div>
							<div class="api-arg-desc">透明度，默认值为 0.5。</div>
						</li>
						<li>
							<div class="api-arg-title">stroke</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">轮廓颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 <code>#ffffff</code>。</div>
						</li>
						<li>
							<div class="api-arg-title">strokeWidth</div>
							<div class="api-arg-type">number</div>
							<div class="api-arg-desc">轮廓宽度，默认值为 0.5。</div>
						</li>
						<li>
							<div class="api-arg-title">lineStyle</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc"><code>undefined</code> (实线)，<code>dashed</code> (虚线) 或者 <code>dotted</code> (点线) 之一。默认值为 undefined。</div>
						</li>
					</ul>
				
{% endapi_method_params %}


### 返回值

<code>MapVisual</code> 对象本身，以便进行链式调用。


{% api_method text 'text, pos, [style]' 0 %}

```javascript
Game.map.visual.text("Target💥", new RoomPosition(11,14,'E2S7'), {color: '#FF0000', fontSize: 10}); 
```

绘制一个文本标签。你可以使用任何有效的 Unicode 字符，包括 <a href="http://unicode.org/emoji/charts/emoji-style.txt" target="_blank">emoji</a>。

{% api_method_params %}
text : string
文本信息
===
pos : <a href="#RoomPosition">RoomPosition</a>
文本基线（baseline）起始点的位置对象。
===
style (可选) : object
包含下列属性的对象：
					<ul>
						<li>
							<div class="api-arg-title">color</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">文本颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 <code>#ffffff</code>。</div>
						</li>
						<li>
							<div class="api-arg-title">fontFamily</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">文本字体，默认为 <code>sans-serif</code></div>
						</li>
						<li>
							<div class="api-arg-title">fontSize</div>
							<div class="api-arg-type">number</div>
							<div class="api-arg-desc">字体大小，基于游戏坐标，默认为 10</div>
						</li>
						<li>
							<div class="api-arg-title">fontStyle</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">字体风格（'normal', 'italic' 或者 'oblique'）</div>
						</li>
						<li>
							<div class="api-arg-title">fontVariant</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">字体变种（'normal' 或者 'small-caps'）</div>
						</li>
						<li>
							<div class="api-arg-title">stroke</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">轮廓颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 undefined（无轮廓）。</div>
						</li>
						<li>
							<div class="api-arg-title">strokeWidth</div>
							<div class="api-arg-type">number</div>
							<div class="api-arg-desc">轮廓宽带，默认为 0.15。</div>
						</li>
						<li>
							<div class="api-arg-title">backgroundColor</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">背景颜色，使用以下格式：<code>#ffffff</code>（十六进制颜色），默认为 undefined（无背景色）。当启用背景色时，文本的垂直对齐模式将被设置为居中（默认为 baseline）。</div>
						</li>
						<li>
							<div class="api-arg-title">backgroundPadding</div>
							<div class="api-arg-type">number</div>
							<div class="api-arg-desc">背景矩形的内边距（padding），默认为 2。</div>
						</li>
						<li>
							<div class="api-arg-title">align</div>
							<div class="api-arg-type">string</div>
							<div class="api-arg-desc">文本对齐，<code>center</code>、<code>left</code>、<code>right</code> 之一。默认为 <code>center</code>。</div>
						</li>
						<li>
							<div class="api-arg-title">opacity</div>
							<div class="api-arg-type">number</div>
							<div class="api-arg-desc">透明度，默认值为 0.5。</div>
						</li>
					</ul>
				
{% endapi_method_params %}


### 返回值

<code>MapVisual</code> 对象本身，以便进行链式调用。


{% api_method clear '' 0 %}

```javascript
Game.map.visual.clear();
```

移除该房间的所有可视化效果。



### 返回值

<code>MapVisual</code> 对象本身，以便进行链式调用。


{% api_method getSize '' 0 %}

```javascript
if(Game.map.visual.getSize() >= 1024000) {
    // 本 tick 无法添加更多的可视化效果
}
```

获取本 tick 所有可视化效果的存储大小。最多不能超过 1024,000（1000 KB）。



### 返回值

可视化效果的大小（单位：字节）。

{% api_method export '' 0 %}

```javascript
Memory.MapVisualData = Game.map.visual.export();
```

返回当前 tick 中添加到地图中的所有可视化效果的紧凑格式。



### 返回值

代表了可视化数据的字符串。除了将其存储以备后续使用外，您不应该对其进行其他操作。

{% api_method import 'val' 0 %}

```javascript
Game.map.visual.import(Memory.MapVisualData);
```

将先前导出（使用<a href="#Game.map-visual.export">Game.map.visual.export</a>）的地图可视化效果添加到当前 tick。 

{% api_method_params %}
val : string
从 Game.map.visual.export 返回的字符串。

{% endapi_method_params %}

### 返回值

<code>MapVisual</code> 对象本身，以便进行链式调用。
