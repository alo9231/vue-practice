  <style>
  </style>
 
<template>
  <div class="menu">
    <a href="" v-for="menu in menuData" :key="menu">{{menu}}</a> 
  </div>

  <!-- 모달 -->
  <div class="black-bg" v-if="modalState == true">  
    <div class="white-bg">
      <h4>{{oneRooms[clickedProduct].title}}</h4>
      <img :src="oneRooms[clickedProduct].image" class="room-img" alt="">
      <p>{{oneRooms[clickedProduct].content}}</p> 
      <p>{{oneRooms[clickedProduct].price}}</p> 
      <button @click="modalState = false">닫기 버튼</button>
    </div>
  </div>
  <!-- //모달 -->

  <!-- <img src="./assets/logo.svg" alt="Vue logo" :style="logo"> -->
  
  <!-- <div v-for="(product, i) in products" :key="i">
    <img :src="product.image" class="room-img" alt="">
    <h4 @click="modalState = true; clickedProduct = i" :style="tblue" >{{product.name}}</h4>
    <p>50 만원</p> 
  </div> -->

    
  <div v-for="(product, i) in oneRooms" :key="i">
    <img :src="product.image" class="room-img" alt="">
    <!-- <h4 @click="modalState = true; clickedProduct = i" :style="tblue" >{{product.name}}</h4> -->
    <h4 @click="modalState = true; clickedProduct = i" :style="tblue" >{{ product.title }}</h4> 
    <p>{{product.price}}</p> 
  </div> 
  
  

</template>

<script>

import room0 from './assets/room0.jpg';
import room1 from './assets/room1.jpg';
import room2 from './assets/room2.jpg';

import oneroomData from './assets/oneroom.js';

export default {
  name : 'App',
  data(){
    return{
      oneRooms : oneroomData,
      modalState : false,
      falseNum : [0,0,0],
      menuData : ['Home', 'Shop', 'About'],
      logo : "display:block; max-height:200px; margin:10px auto;",    
      tblue : "color: #2f61bf",  
      products: [
        { name: '역삼동원룸', image: room0, reportCount: 0, clickedProduct: 0 },
        { name: '천호동원룸', image: room1, reportCount: 0, clickedProduct: 1},
        { name: '마포구원룸', image: room2, reportCount: 0, clickedProduct: 2 }
      ],    
    }
  },
  methods : {
    increase(i){
      this.falseNum[i] += 1;
    },
  },
  components : {
  }
}
</script>

<style>
</style> 