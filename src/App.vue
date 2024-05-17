<template>
  <!-- <div class="black-bg" v-if="openModal == true">
    <div class="white-bg">
      <h4>{{onerooms[clickData].title}}</h4>
      <img :src="onerooms[clickData].image" alt="" class="room-img">
      <p>{{onerooms[clickData].content}}</p>
      <p>{{onerooms[clickData].price}}</p>
      <Discount/>
      <button @click="openModal = false">닫기</button>
    </div>
  </div> -->
  <transition name="fade">
    <Modal
      @openModal="openModal = false"
      :onerooms="onerooms"
      :clickData="clickData"
      :openModal="openModal"
    />
  </transition>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <!-- <div class="discount">
    <h4>지금 결제하면 20% 할인</h4>
  </div> -->

  <Discount />

  <button @click="priceSortAscending">가격낮은순정렬</button>
  <button @click="priceSortDescending">가격높은순정렬</button>
  <button @click="priceSortAlphabet">가나다순정렬</button>

  <button @click="sortBack">되돌리기</button>

  <!-- <div v-for="(oneroom, i) in onerooms" :key="i">
    <img :src="onerooms[i].image" alt="" class="room-img" />
    <h4
      @click="
        openModal = true;
        clickData = i;
      "
    >
      {{ oneroom.title }}
    </h4>
    <p>{{ oneroom.price }}원</p>
  </div> -->

  <Card
    @openModal="
      openModal = true;
      clickData = $event;
    "
    :oneroom="onerooms[i]"
    v-for="(oneroom, i) in onerooms"
    :key="i"
  />
  <!-- <Card :oneroom="onerooms[1]" />
  <Card :oneroom="onerooms[2]" />
  <Card :oneroom="onerooms[3]" />
  <Card :oneroom="onerooms[4]" />
  <Card :oneroom="onerooms[5]" /> -->

  <!-- 
  <div>
    <img src="./assets/room1.jpg" alt="" class="room-img">
    <h4>{{products[1]}}</h4>
    <p>70 만원</p>
    <button @click="신고수[1]++">허위매물신고</button>
    <span>신고수 : {{신고수[1]}}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" alt="" class="room-img">
    <h4>{{products[2]}}</h4>
    <p>90 만원</p>
    <button @click="신고수[2]++">허위매물신고</button>
    <span>신고수 : {{신고수[2]}}</span>
  </div> -->
</template>

<script>
import data from "./assets/oneroom.js";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      showDiscount: true,
      oneroomsOriginal: [...data],
      clickData: 0,
      onerooms: data,
      openModal: false,
      신고수: [0, 0, 0],
      menus: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase() {
      this.신고수++;
    },

    priceSortAscending() {
      this.onerooms.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    priceSortDescending() {
      this.onerooms.sort(function (a, b) {
        return b.price - a.price;
      });
    },
    priceSortAlphabet() {
      this.onerooms.sort(function (a, b) {
        return a.title > b.title ? 1 : -1;
      });
    },
    sortBack() {
      this.onerooms = [...this.oneroomsOriginal];
    },
  },
  mounted() {
    // setTimeout(() => {
    //   this.showDiscount = false;
    // }, 2000);
    // setInterval(() => {
    //   this.intervalDiscount--;
    //   if (this.intervalDiscount <= 0) {
    //     this.intervalDiscount = 0;
    //   }
    // }, 1000);
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 15px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
