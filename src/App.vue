<template>

<!-- nav -->
  <div class="menu">
    <!-- :key=""의 용도 
          반복문 사용시 꼭 써야함 반복문 돌린 요소를 컴퓨터가 구분하기 위해 사용-->
    <a v-for="(menuList, i) in menu" :key="i"> {{ menuList }} </a>  
  </div>

  <div v-for="(productsList, i) in products" :key="i">
    <h4>{{products[i]}}</h4>
    <p>50 만원</p>
  </div> 
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      menu : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
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
