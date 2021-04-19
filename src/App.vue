<template>
  <div class="black-bg" v-show="modalYn == true">
    <div class ="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
        <button @click="modalYn=false">닫기</button>
    </div>
  
  </div>
  <div class="menu">
    <a>Home</a>
    <a>Prodect</a>
    <a>Home</a>
    <a v-for="product in products" :key="product">{{product}}</a>
  </div>
  <img alt="Vue logo" src="./assets/logo.png">
  <div v-for="(a,i) in products" :key="i">
    <img :src="'./static/room'+i+'.jpg'" class="room-img"/>
    <h4 @click="modalYn = true">{{a}}</h4>
    <h4>{{prices[i]}}</h4>
    <button @click="declarationCnt[i]++">허위매물신고</button><span> 신고 수 :{{declarationCnt[i]}}</span>
  </div>
   <div v-for="(a,i) in rooms" :key="i">
    <img :src="rooms[i].image" class="room-img"/>
    <h4>{{rooms[i].title}}</h4>
    <p>{{rooms[i].content}}</p>
    <p>{{rooms[i].price}}원</p>
    
  </div>
</template>

<script>

import roomData from './assets/roomData.js'

export default {
  name: 'App',
  data(){
    return {
      rooms : roomData,
      modalYn : false,
      declarationCnt : [0,0,0],
      prices : [1000,2000,300],
      products : ['역삼동원룸','천호동원룸','마포구원룸']
    }
  },
  methods: {
    callDeclarationCnt(){
      this.declarationCnt++;
       //alert(declarationCnt);
    }
    ,getImg(i){
      return "./assets/room"+i+".jpg";
    }
    ,modal(){
      alert(this.modalYn);
      if(this.modalYn == true){
        this.modalYn = false;
      }else{
        this.modalYn = true;
      } 
      
    }

  },
  components: {
  
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
body{
  margin : 0
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position:fixed;padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
