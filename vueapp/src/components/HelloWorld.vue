<template>
  <div class="hello">
    <H2>출력창</H2>
    <h1>{{this.msg}}</h1>
    <button @click="callTest('firstAttribute')">FIRST</button>
    <br>
    <br>
    <button @click="callTest('secondAttribute')">SECOND</button>
    <br>
    <br>
    <div v-for="board in my_boards" :key=board>
      <h2>{{board[0]}}</h2>
      <h4>{{board[1]}}</h4>
    </div>
    <button @click="getBoardList">BOARD</button>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: "0",
      my_boards:[]
    }
  },
  methods:{
    callTest(pick){
      console.log("clicked")
      axios({
        method: "get",
        url: "/test"
      }).then((response)=>{
        console.log(response)
        this.msg = response.data[pick]
      })
    },
    getBoardList(){
      console.log("clicked")
      axios({
        method: "get",
        url: "/board/list"
      }).then((response)=>{
        console.log(response)
        this.my_boards = response.data['boards']
      })
    }
  }
}
</script>