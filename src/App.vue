<template>

  <div class="black-bg" v-if="openModal == true">
    <div class="white-bg">
      <h4>{{onerooms[clickData].title}}</h4>
      <img :src="onerooms[clickData].image" alt="" class="room-img">
      <p>{{onerooms[clickData].content}}</p>
      <p>{{onerooms[clickData].price}}</p>
      <button @click="openModal = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{menu}}</a>
  </div>

  <div v-for="(oneroom, i) in onerooms" :key='i'>
    <img :src="onerooms[i].image" alt="" class="room-img">
    <h4 @click="openModal = true; clickData = i">{{oneroom.title}}</h4>
    <p>{{oneroom.price}}원</p>
  </div>

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

import data from './assets/oneroom.js'

export default {
  name: 'App',
  data(){
    return{
      clickData : 0,
      onerooms : data,
      openModal : false,
      신고수 : [0,0,0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸']
    }
  },
  methods : {
    increase(){
      this.신고수++;
    }
  },
  components: {
  }
}
</script>

<style>

body{
  margin: 0
}

div{
  box-sizing: border-box
}

.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg{
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

.menu{
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 15px
}

.menu a{
  color: white;
  padding: 10px
}

.room-img{
  width: 100%;
  margin-top: 40px
}
</style>
