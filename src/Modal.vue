<template>
  <div class="black-bg" v-if="openModal == true">
    <div class="white-bg">
      <h4>{{ onerooms[clickData].title }}</h4>
      <img :src="onerooms[clickData].image" alt="" class="room-img" />
      <p>{{ onerooms[clickData].content }}</p>
      <!-- <Discount /> -->
      <input v-model.number="month" />
      <!-- <input type="range" min="1" max="12" /> -->
      <p>{{ month }}개월 선택함 : {{ onerooms[clickData].price * month }} 원</p>
      <button @click="send">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal-a",
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(a) {
      if (a >= 13) {
        alert("안됨");
        this.month = 1;
      } else if (isNaN(a) == true) {
        alert("숫자로만 입력하세요");
        this.month = 1;
      }
    },
  },
  props: {
    onerooms: Array,
    clickData: Number,
    openModal: Boolean,
  },
  methods: {
    send() {
      this.$emit("openModal");
    },
  },
};
</script>

<style></style>
