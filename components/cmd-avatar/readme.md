### Avatar 头像

头像组件，组件名：``cmd-avatar``，代码块： cmdAvatar。

**使用方式：**

在 ``script`` 中引用组件 

```javascript
import cmdAvatar from "@/components/cmd-avatar/cmd-avatar.vue"
export default {
    components: {cmdAvatar}
}
```

基本用法

```html
<cmd-avatar src='http://www.xx.xx/xx/x.jpg'></cmd-avatar>
<cmd-avatar icon='add'></cmd-avatar>
<cmd-avatar text='U'></cmd-avatar>
```

文字/图标样式设置

```html
<cmd-avatar :make="{'color': '#f56a00','background-color': '#fde3cf'}" text='1'></cmd-avatar>
<cmd-avatar :make="{'color': '#f56a00','background-color': '#fde3cf'}" icon='add'></cmd-avatar>
```

大小设置

```html
<cmd-avatar size='sm' :src='img'></cmd-avatar>
<cmd-avatar size='md' :src='img'></cmd-avatar>
<cmd-avatar size='100' :src='img'></cmd-avatar>
<cmd-avatar size='lg' :src='img'></cmd-avatar>
```

形状设置

```html
<cmd-avatar shape='square' :src='img'></cmd-avatar>
<cmd-avatar shape='circle' :src='img'></cmd-avatar>
```


**属性说明：**

|属性名	|类型					|默认值				|说明															|
|---		|----					|---					|---															|
|text		|String,Numbar|-						|显示文字													|
|icon		|String				|-						|显示图标icon											|
|src		|String				|-						|图片地址													|
|shape	|Eume					|'circle'			|形状 圆形'circle' ，矩形'square'	|
|size		|Eume,Numbar	|'md'					|大小 sm,md,lg,任意Number值				|
|make		|Object				|{'color': ''}|自定义样式												|

**事件说明：**

|事件名称	|说明										|
|---			|---										|
|click		|点击 Avatar 触发事件		|
|load			|图片载入成功后触发事件	|
|error		|图标载入错误后触发事件	|
