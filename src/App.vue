<template>

<!-- : == v-bind -->

<!-- props로 자식에게 데이터 보냄  -->
<Modal :roomInfo="roomInfo" :click="click" :modalOpen="modalOpen"/>

<!-- nav -->
  <div class="menu">
    <!-- :key=""의 용도 
    반복문 사용시 꼭 써야함 반복문 돌린 요소를 컴퓨터가 구분하기 위해 사용-->
    <a v-for="(menuList, i) in menu" :key="i"> {{ menuList }} </a>  
  </div>

  <Discount/>

  <Card :roomInfo="roomInfo" />

  <!-- <div v-for="(productsList, i) in products" :key="i">
    <h4>{{products[i]}}</h4>
    <p>50 만원</p>
  </div>  -->
</template>

<script>

import {data} from './assets/oneRoom'
import Modal from './Modal.vue'
import Discount from './Discount.vue'
import Card from './Card.vue'


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
    Discount : Discount,
    Modal : Modal,
    Card : Card,
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

.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
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
