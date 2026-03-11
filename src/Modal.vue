<template>
  <div class="black-bg" v-if="modalState == true">
    <div class="white-bg shadow-lg">
      <h4>{{ oneRooms[clickedProduct].title }}</h4>
      <img :src="oneRooms[clickedProduct].image" class="room-img" />
      <p>{{ oneRooms[clickedProduct].content }}</p>
      <input type="text" v-model="month" class="border-2 border-indigo-500" />
      <p>{{ month }} 개월 선택함 : {{ oneRooms[clickedProduct].price * month }}원</p>
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
  data() {
    return {
      month: 1,
    }
  },
  beforeUpdate() {
    if (this.month == 2) {
      alert('2개월은 너무 적음.. 안팝니다')
    }
  },
  watch: {
    month(a) {
      // ex: (a,b) => a는 변경후 데이터 | b는 변경전 데이터
      if (isNaN(a) || a.trim() === '') {
        alert('숫자만 입력가능')
        a.value = 1
      }
    },
  },
  props: {
    oneRooms: Array,
    modalState: Boolean,
    clickedProduct: Number,
  },
}
</script>
<style></style>
