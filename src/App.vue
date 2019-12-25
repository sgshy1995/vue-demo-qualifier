<template>
  <div id="app">
    <h1>Vue</h1>
    <hr>
    <h2>for(value,key) in array or object 且 key:key</h2>
    <ol>
      <li v-for="(u,index) in users" :key="index">姓名：<span class="data">{{index}}</span>，性别：<span class="data">{{u}}</span></li>
    </ol>
    <hr />
    <h2>修饰符</h2>
    <h3>stop 修饰符：阻止事件传播/冒泡</h3>    
    <div id="father-div" @click="fatherEl">
      <button @click="childEl1">子元素事件1(正常)</button>
      <button @click.stop="childEl2">子元素事件2(stop)</button>
      <span>点击前请打开控制台</span>
    </div>
    <h3>prevent 修饰符：阻止默认事件</h3>
    <div id="prevent-div">
      <a href="https://baidu.com" @click.prevent="preventEl">百度</a>
    </div>
    <h3>按键修饰符</h3>
    <div id="key-div">
      <input type="text" @keyup.enter="enterEl" placeholder="监听回车">
      <input type="text" @keyup.delete="deleteEl" placeholder="监听删除/回退">
    </div>
    <h3>sync 修饰符</h3>
    <span style="color:red">:money.sync="total"</span> === <span style="color:red">:money="total" v-on:update:money="total=$event"</span>
    <div id="sync-div">
      爸爸有这些钱：<span class="data">{{total}}</span>
      <Child :money.sync="total" />
    </div>
  </div>
</template>

<script>
import Child from './components/child.vue'
export default {
  data(){
    return{
      users:{
        Sgs:'male',
        Eden:'female',
        John:'male',
        Lily:'female'
      },
      total:10000
    }
  },
  components:{
    Child: Child
  },
  methods:{
    fatherEl(){
      console.log('父元素事件触发了')
    },
    childEl1(){
      console.log('子元素事件1触发了')
    },
    childEl2(){
      console.log('子元素事件2触发了')
    },
    preventEl(){
      console.log('你被阻止了')
    },
    enterEl(){
      alert('你按了回车')
    },
    deleteEl(){
      alert('你按了删除')
    }
  }
}

</script>


<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
#app #father-div{
  border: 1px solid black;
  padding: 10px;
}
#app #father-div > button{
  margin: 5px;
}
#app #prevent-div{
  padding: 10px;
  border: 1px solid black;
}
#app #key-div{
  padding: 10px;
  border: 1px solid black;
}
#app #key-div > input{
  margin: 5px;
}
#app #sync-div{
  padding: 10px;
  border: 1px solid black;
}
span.data{
  color: darkgray;
  margin: 5px;
}
span{
  cursor: default;
}
button{
  cursor: pointer;
}
</style>
