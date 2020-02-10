
# StructureSpawn.Spawning

当前正在孵化的 creep 的详细信息，可以通过[`StructureSpawn.spawning`](#StructureSpawn.spawning)属性进行访问。

{% api_property directions 'array<number>' %}

一个指示了出生方向的数组，参见 [`StructureSpawn.Spawning.setDirections`](#StructureSpawn.Spawning.setDirections).

{% api_property name 'string' %}

新 creep 的名字。

{% api_property needTime 'number' %}

完成孵化总共需要的时间。

{% api_property remainingTime 'number ' %}

剩下的时间。

{% api_property spawn '<a href="#StructureSpawn">StructureSpawn</a>' %}

一个到对应 spawn 的链接。


{% api_method cancel '' A %}

```javascript
Game.spawns['Spawn1'].spawning.cancel();
```

立即取消孵化。不返还消耗的资源。

### Return value

如下错误码之一：
{% api_return_codes %}
OK | 这个操作已经成功纳入计划。
ERR_NOT_OWNER | 你不是该 spawn 的所有者。
{% endapi_return_codes %}

{% api_method setDirections 'directions' A %}

```javascript
Game.spawns['Spawn1'].spawning.setDirections([RIGHT, TOP_RIGHT]);
```

设置出生方向，以使它们在生成时应移动到的位置。

{% api_method_params %}
directions : array&lt;number>
包含如下方向常量的数组:
    <ul>
        <li><code>TOP</code></li>
        <li><code>TOP_RIGHT</code></li>
        <li><code>RIGHT</code></li>
        <li><code>BOTTOM_RIGHT</code></li>
        <li><code>BOTTOM</code></li>
        <li><code>BOTTOM_LEFT</code></li>
        <li><code>LEFT</code></li>
        <li><code>TOP_LEFT</code></li>
    </ul>
{% endapi_method_params %}

### Return value

如下错误码之一：
{% api_return_codes %}
OK | 这个操作已经成功纳入计划。
ERR_NOT_OWNER | 你不是该 spawn 的所有者。
ERR_INVALID_ARGS | 无效的方向数组
{% endapi_return_codes %}
