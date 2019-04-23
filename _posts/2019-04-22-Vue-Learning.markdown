---
layout:     post
title:      "Vue Learning"
subtitle:   " \"Vue learning\""
date:       2019-04-22 18:23:00
author:     "王琼弟"
catalog: true
tags:
    - 前端
    - Vue
---

#### 简单的开始

导入js:<https://cdn.staticfile.org/vue/2.2.2/vue.min.js>

```python
	<div id="app">
		{{message}}
	</div>
	<script>
		new Vue({
			el:"#app",
			data:{
				message:"Hello"
			}
		})
	</script>
```

#### 一些操作

v-for="(value,key,index) in Object" 参数顺序为值，键，索引。

```python
	<div id="app">
		<li v-for="(value,key,index) in Object">
			{{index}}:{{key}}:{{value}}
		</li>
	</div>
	<script>
		new Vue({
			el:"#app",
			data:{
				Object:{
					name:"sadasd",
					value:20
				}
			}
		})
	</script>
```

0:name:sadasd

1:value:20



