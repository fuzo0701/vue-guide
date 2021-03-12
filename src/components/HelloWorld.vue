<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ message }}</h2>

    <span v-bind:title="tit_message"> 내 위에 잠시 마우스를 올리면 동적으로 바인딩 된 title을 볼 수 있습니다.</span>
    <p v-if="seen">이제 나를 볼수 있어요</p>

    <div id="demo">
      <button v-on:click="show =! show"> Toggle </button>
      <transition name="fade">
        <p v-if="show">hello</p>
      </transition>
    </div>

    <div id="todoList">
      <ol>
        <li v-for="(todo, i) in todos" :key="i">
         {{ todo.text }}
        </li>
      </ol>
    </div>

    <div id="reverse">
      <p>{{reverseMsg}}</p>
      <button v-on:click="reverseMessage">메시지 뒤집기</button>
    </div>

    <div id="app-6">
      <p> {{ appMessage }} </p>
      <input v-model="appMessage">
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      message : '안녕하세요 Vue!',
      tit_message : '이 페이지는 ' + new Date() + ' 에 로드 되었습니다.',
      seen: false,
      show: true,
      reverseMsg : '안녕하세요! Vue.js!',
      todos : [
        { id:0 , text : 'JavaScript 배우기'},
        { id:1 , text : 'Vue 배우기'},
        { id:2 , text : '무언가 멋진 것을 만들기'}
      ],
      appMessage : '안녕하세요!! 6'
    }
  },
  methods : {
    reverseMessage: function(){
      this.reverseMsg = this.reverseMsg.split('').reverse().join('')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
