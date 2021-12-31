<template>

<!-- props로 자식에게 데이터 보냄  -->
<!-- v-bind == : -->

<transition name="fade">
  <Modal @openModal="modalOpen = false" :roomInfo="roomInfo" :click="click" :modalOpen="modalOpen"/> 
</transition>

<!-- nav -->
  <div class="menu">
    <!-- :key=""의 용도 
    반복문 사용시 꼭 써야함 반복문 돌린 요소를 컴퓨터가 구분하기 위해 사용-->
    <a v-for="(menuList, i) in menu" :key="i"> {{ menuList }} </a>  
  </div>

  <Discount />




  <button @click="priceSort">가격순정렬</button>
  <button @click="priceReverseSort">가격역순정렬</button>
  <button @click="sortHanguel">가나다순정렬</button>
  <button @click="sortBack">되돌리기</button>
  

  <Card @openModal="modalOpen = true; click = $event" :roomInfo="roomInfo[i]" v-for="(room, i) in roomInfo" :key="room" />

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
      showDiscount : true,
      roomInfoOrigin : [...data], //JavaScript: [...]사본
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
    },

    priceSort(){
      this.roomInfo.sort((a, b) => {
        return a.price - b.price;
      })
    },

    priceReverseSort(){
      this.roomInfo.sort((a, b) => {
        return b.price - a.price;
      })
    },

    sortHanguel(){
      this.roomInfo.sort((a, b) => {
        let x = a.title.toLowerCase();
        let y = b.title.toLowerCase();

        if(x < y) return -1;
        if(x > y) return 1;
      });
    },
    
    sortBack(){
      this.roomInfo = [...this.roomInfoOrigin];
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
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}



.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}




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
