<template>
  <div class="discount">
    <h4>지금 결제하면 {{ amount }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'Discount',
  data() {
    return {
      amount: 30,
      timer: null,
    }
  },
  watch: {
    // amount의 변화를 감시합니다.
    amount(newValue) {
      if (newValue <= 0) {
        // 부모에게 'closeDiscount'라는 이벤트를 보냅니다.
        this.$emit('closeDiscount')
        clearInterval(this.timer) // 타이머도 종료
      }
    },
  },
  mounted() {
    setInterval(() => {
      this.amount--
    }, 1000)
  },
}
</script>
<style></style>
