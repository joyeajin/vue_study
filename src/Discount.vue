<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discountNum }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: "Discount-a",
  data() {
    return {
      discountNum: 5,
    };
  },
  mounted() {
    setInterval(() => {
      this.discountNum--;
      if (this.discountNum <= 0) {
        this.discountNum = 0;
      }
    }, 1000);
  },
};
</script>

<style></style>
