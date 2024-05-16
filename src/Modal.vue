<template>
  <div class="black-bg" v-if="openModal == true">
    <div class="white-bg">
      <h4>{{ onerooms[clickData].title }}</h4>
      <img :src="onerooms[clickData].image" alt="" class="room-img" />
      <p>{{ onerooms[clickData].content }}</p>
      <p>{{ onerooms[clickData].price }}</p>
      <Discount />
      <!-- <button @click="openModal = false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal-a",
  props: {
    onerooms: Array,
    clickData: Number,
    openModal: Boolean,
  },
};
</script>

<style></style>
