## Vue生命周期

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <style></style>
  </head>
  <body>
    <div id="app">
      <label>生日</label>
      <input type="date" v-model="birthday" />
      <div>当前用户{{ getAge }}周岁了</div>
      <custom-el v-if="show">
        <span>测试测试测试</span>
      </custom-el>
    </div>
    <script>
      //监听全局异常
      Vue.config.errorHandler = function(err, vm, info) {
        console.log(err);
      };
      //自定义元素，用于测试销毁元素生命周期
      Vue.component("custom-el", {
        data: function() {
          return {
            msg: "dddddddd",
          };
        },
        created: function() {
          //抛出错误，验证 异常捕获钩子
          throw new Error("测试异常捕获钩子");
        },
        template: `
          <div>
            <span>{{msg}}</span>
            <slot></slot>
          </div>
        `,
      });

      var app = new Vue({
        el: "#app",
        data: function() {
          return {
            birthday: "2010-10-10",
            show: true,
          };
        },
        beforeCreate: function() {
          //创建之前，无法拿到 $data 与 $el
          console.log("beforeCreate");
          console.log(this.birthday);
          console.log(this.$el);
        },
        created: function() {
          //创建之前，只能拿到$data ，但无法拿到$el
          console.log("created");
          console.log(this.birthday);
          console.log(this.$el);
        },
        beforeMount: function() {
          //挂载之前，可以拿到$data与$el，但是$el是未解析的虚拟dom
          console.log("beforeMount");
          console.log(this.birthday);
          console.log(this.$el);
        },
        mounted: function() {
          console.log(this);
          //挂载之后，可以拿到$data与$el,此时$el为已被解析的真实dom
          console.log("beforeMount");
          console.log(this.birthday);
          console.log(this.$el);
        },
        beforeUpdate: function() {
          //在$data已经修改，但是组件dom并未更新渲染时调用
          console.log("beforeUpdate");
          console.log(JSON.stringify(this.$data)); //新的数据
          console.log(this.$el.innerHTML); //原始dom
        },
        updated: function() {
          //在$data已经修改，组件dom已被重新渲染之后调用
          console.log("updated");
          console.log(JSON.stringify(this.$data)); //新的数据
          console.log(this.$el.innerHTML); //新的dom,不能保证所有子组件被重新渲染
          this.$nextTick(function() {
            console.log(this.$el.innerHTML); //新的dom,可以保证所有子组件被重新渲染了
          });
        },
        //此处存在问题，并未验证出来beforeDestroy与destroyed的区别
        beforeDestroy: function() {
          //实例销毁之前被调用，这一步，实例仍然完全可用
          console.log("beforeDestroy");
          this.birthday = "2014-11-11";
        },
        destroyed: function() {
          //Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，
          //所有的事件监听器会被移除，所有的子实例也会被销毁。
          console.log("destroyed");
        },
        errorCaptured: function(err, vm, info) {
          //当捕获一个来自子孙组件的错误时被调用
          console.error(err);
          //如果返回false，则会阻止错误继续向上传播，否则会被全局errorHandler捕获
          return true;
        },
        methods: {},
        computed: {
          getAge: function() {
            if (this.birthday) {
              let date = new Date();
              let birth = new Date(this.birthday);
              let m1 = date.getMonth();
              let m2 = birth.getMonth();
              let et = m1 > m2 ? 0 : 1;
              if (m1 == m2 && data.getDate() > birth.getDate()) {
                et = 0;
              }
              return date.getFullYear() - birth.getFullYear() - et;
            }
            return 0;
          },
        },
        filters: {},
      });
    </script>
  </body>
</html>

```

