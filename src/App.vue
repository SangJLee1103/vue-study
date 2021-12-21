<template>


<!-- modal -->
<div class="black-bg" v-if="modalOpen == true">
  <div class="white-bg"> 
    <img :src="roomInfo[click].image" class="room-img">
    <h4>{{roomInfo[click].title}}</h4>
    <p>{{roomInfo[click].content}}</p>
    <button @click="modalOpen = false">닫기</button>
  </div>
</div>

<!-- nav -->
  <div class="menu">
    <!-- :key=""의 용도 
    반복문 사용시 꼭 써야함 반복문 돌린 요소를 컴퓨터가 구분하기 위해 사용-->
    <a v-for="(menuList, i) in menu" :key="i"> {{ menuList }} </a>  
  </div>


  <div v-for="(room, i) in roomInfo" :key="i">
    <img :src="roomInfo[i].image" class="room-img">
    <h4 @click="modalOpen = true; click = i">{{roomInfo[i].title}}</h4>
    <p>{{roomInfo[i].price}}</p>
    <!-- v-on과 @는 같음 -->
  </div>

  <!-- <div v-for="(productsList, i) in products" :key="i">
    <h4>{{products[i]}}</h4>
    <p>50 만원</p>
  </div>  -->
</template>

<script>

import {data} from './assets/oneRoom'

export default {
  name: 'App',
  data(){ //react에서는 state라고 함
    return {
      click : 0,
      roomInfo : data,
      modalOpen : false,
      count: [0, 0, 0],
      menu : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods : {
    increase(i){
      this.count[i]++;
    }
  },

  components: {
  }
}
</script>

<style>

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}


.room-img{
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu { 
  background:  darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 10px;
}
</style>
