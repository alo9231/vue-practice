<style></style>

<template>
  <Discount v-if="showDiscount == true" @closeDiscount="showDiscount = false" />
  <button
    @click="priceSort()"
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold mr-2 py-2 px-4 rounded"
  >
    가격낮은순 정렬
  </button>
  <button
    @click="priceSort2()"
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold mr-2 py-2 px-4 rounded"
  >
    가격높은순 정렬
  </button>
  <button
    @click="priceSort3()"
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold mr-2 py-2 px-4 rounded"
  >
    가나다순 정렬
  </button>

  <button
    @click="priceSortBack()"
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold mr-2 py-2 px-4 rounded"
  >
    되돌리기
  </button>

  <!-- 모달 -->
  <transition name="fade">
    <Modal
      :oneRooms="oneRooms"
      :modalState="modalState"
      :clickedProduct="clickedProduct"
      @closeModal="modalState = false"
    />
  </transition>

  <!-- //모달 -->

  <!-- <img src="./assets/logo.svg" alt="Vue logo" :style="logo"> -->

  <!-- <div v-for="(product, i) in products" :key="i">
    <img :src="product.image" class="room-img" alt="">
    <h4 @click="modalState = true; clickedProduct = i" :style="tblue" >{{product.name}}</h4>
    <p>50 만원</p>
  </div> -->

  <div v-for="(product, i) in oneRooms" :key="i">
    <img :src="product.image" class="room-img" alt="" />
    <!-- <h4 @click="modalState = true; clickedProduct = i" :style="tblue" >{{product.name}}</h4> -->
    <h4 @click="openModal(i)" :style="tblue" class="ring-2 ring-blue-500 inline-block m-8 p-2">
      {{ product.title }}
    </h4>
    <p class="block">{{ product.price }}</p>
  </div>
</template>

<script>
import room0 from './assets/room0.jpg'
import room1 from './assets/room1.jpg'
import room2 from './assets/room2.jpg'

import oneroomData from './assets/oneroom.js'
import Discount from './Discount.vue'
import Modal from './Modal.vue'

export default {
  name: 'App',
  data() {
    return {
      showDiscount: true,
      oneRoomsOrigin: [...oneroomData],
      clickedProduct: 0,
      oneRooms: oneroomData,
      modalState: false,
      falseNum: [0, 0, 0],
      menuData: ['Home', 'Shop', 'About'],
      logo: 'display:block; max-height:200px; margin:10px auto;',
      tblue: 'color: #2f61bf; cursor: pointer;',
      products: [
        { name: '역삼동원룸', image: room0, reportCount: 0, clickedProduct: 0 },
        { name: '천호동원룸', image: room1, reportCount: 0, clickedProduct: 1 },
        { name: '마포구원룸', image: room2, reportCount: 0, clickedProduct: 2 },
      ],
    }
  },
  methods: {
    increase(i) {
      this.falseNum[i] += 1
    },
    openModal(i) {
      console.log('클릭된 인덱스:', i)
      this.modalState = true
      this.clickedProduct = i
    },
    priceSortBack() {
      this.oneRooms = [...this.oneRoomsOrigin]
    },
    priceSort() {
      this.oneRooms.sort(function (a, b) {
        return a.price - b.price
      })
    },
    priceSort2() {
      this.oneRooms.sort(function (a, b) {
        return b.price - a.price
      })
    },
    priceSort3() {
      this.oneRooms.sort(function (a, b) {
        if (a.title > b.title) {
          return 1
        } else {
          return -1
        }
      })
    },
  },
  mounted() {
    // setTimeout(() => {
    //   this.showDiscount = false
    // }, 2000)
  },
  components: {
    Discount: Discount,
    Modal: Modal,
  },
}
</script>

<style></style>
