# 1. vue中的ref和$refs

- 获取DOM元素，需document.querySelector(".input1")获取这个dom节点，后再获取input1的值。

- 但是用ref绑定之后，就不需要再获取dom节点，直接在input上绑定input1，然后在$refs里面调用。

- 在javascript里面这样调用: this.$refs.input1 这样就可减少获取dom节点的消耗

用法如下:

```javascript
<div id="app">
  <input type="text" ref="input1"/>
  <button @click="add">添加</button>
</div>
<script>
	new Vue({
		el: "#app",
    methods:{
    	add(){
      	this.$refs.input1.value = "test"
    	}
    }
  })
</script>
```







