BootStrap 响应式布局


vue.js 数据驱动 该数据让页面出现想要的样子
 搭建步骤：
  1.引入vue.js
   远程url，本地下载
  2.创建容器div
   <div id="app">
  3.实例化
  <script>
    var app = new Vue({
        el:'#app' --容器选择器
        data:
            });
  </script>

条件显示：
  v-if指令

循环显示（数组）：
 v-for指令
   <div id="app">
      <ul>
         <li v-for="h in hobby">{{h}}</li>
      </ul>
   </div>

    <script>
      var app = new Vue({
        el:'app',
        data:{
          hobby:['篮球','足球','羽毛球','乒乓球']
        }
      })；
    </script>

循环显示（对象）：
     v-for指令
       <div id="app">
          <ul>
             <li v-for="user in users">{{user.name}}-----{{user.sex}}</li>
          </ul>
       </div>

        <script>
          var app = new Vue({
            el:'app',
            data:{
              users:[
              {'name':'AA','sex':'0'},
              {'name':'BB','sex':'1'},
              {'name':'CC','sex':'2'},
              ]
            }
          })；
        </script>

用户输入（双向绑定）
  v-model指令

  <div id="app">
    <h2>{{msg}}</h2>
    <input type="text" v-model="msg">
  </div>

  <script>
     var app = new Vue({
       el:'app',
       data:{
         msg:''
       }
     })；
  </script>

事件处理
  @click
  @mouseover 鼠标选择上
  @mouseout 鼠标离开
  methods属性

  给test加上css样式
      <style>
        #test{
          width:200px; 宽
          height:200px; 高
          border:solid 1px #ddd; 边框
        }
        .active{ 声明class
          background-color: #def  鼠标移动 切换样试时的背景颜色
        }
      </style>

    <div id="app">
      <div id="test" @click="run" ：class="cls" @mouseover="mover" @mouseout="mout"> 给test绑定事件
    </div>

    <script>
       var app = new Vue({
         el:'app',
         data:{
         cls:''
         },
         methods:{
           run:function(){
            alert('你点了我一下')；
           },
           mover:function(){
            this.cls="active"
           },
           mout:funcation(){
            this.cls="";
           }
         }
       })；
    </script>

 计算属性
  computed

  <div id="app">
    <table>
      <tr><td>ID</td><td>单价</td><td>数量</td><td>小结</td></tr>
      <tr><td>1</td><td>{{price}}</td><td>{{num}}</td><td></td></tr>
    </table>
  </div>

  <script>
     var app = new Vue({
       el:'app',
       data:{
         msg:''
       }
     })；
  </script>
