<template>
<div>
<!--데이터 바인딩을 왜 하는가?
    - HTML에 하드코딩해놓으면 나중에 변경이 어려움
    - Vue의 실시간 자동 렌더링 쓰려면 하셈 
      - 렌더링이란 data 와 관련된 데이터를 빠르게 반영되는것을 의미한다.
    
      -->
  <div class="black-bg" @click="모달창열렸니=false" v-if = "모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="menu in menuList" :key="menu">{{menu}}</a>
  </div>
  
  <div v-for="(room,i) in (원룸들)" :key="i">
    <img class="room-img" :src="room.image" >
    <h4 class="red" :style="스타일" @click="모달창열렸니=true">{{room.title}}</h4>
    <p> {{room.price}} 만원</p>
  </div>
</div>
</template>

<script>
import oneroom from "./assets/data.js";

export default {
  name: 'App',
  data(){
    return {
      원룸들 : oneroom,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      }
  },
  methods : {
    increase(i){
      this.신고수[i] += 1;
    }
  },
  components: {
  }
}
</script>

<style>
body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: (0.0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px ;

}
.menu a{
  color: white;
  padding: 10px;

}
.room-img{
  width: 100%;
  margin-top: 40px;
}

</style>
