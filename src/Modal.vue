<template>
  <div class="black-bg" v-if="modalState == true">
    <div class="white-bg shadow-lg">
      <h4>{{ oneRooms[clickedProduct].title }}</h4>
      <img :src="oneRooms[clickedProduct].image" class="room-img" />
      <p>{{ oneRooms[clickedProduct].content }}</p>
      <p>{{ oneRooms[clickedProduct].price }}원</p>
      <button
        class="bg-blue-500 shadow-lg shadow-blue-500/50 text-white p-2"
        @click="$emit('closeModal')"
      >
        닫기
      </button>
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
