<template>
  <div class="black-bg" v-if="modalState == true">
    <div class="white-bg">
      <h4>{{ oneRooms[clickedProduct].title }}</h4>
      <img :src="oneRooms[clickedProduct].image" class="room-img" />
      <p>{{ oneRooms[clickedProduct].content }}</p>
      <p>{{ oneRooms[clickedProduct].price }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    oneRooms: Array,
    modalState: Boolean,
    clickedProduct: Number,
  },
}
</script>
<style></style>
