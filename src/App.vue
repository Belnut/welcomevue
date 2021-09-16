<template>
  <div class="black-bg" v-if="isModalOpened">
    <div class="white-bg">
      <h4>{{ target.title }}</h4>
      <img :src="target.image" class="room-img">
      <p>{{ target.content }}</p>
      <p>{{ target.price }}</p>
      <button @click="isModalOpened = false">닫기</button>
    </div>  
  </div>


  <div class="menu">
    <a v-for="(작명, i) in menus" :key="i">{{작명}} </a>
  </div>



  <div v-for="(oneroom, i) in onerooms" :key="i">
    <img :src="oneroom.image" class="room-img">
    <h4 @click="openModal(i)">{{oneroom.title}}</h4>
    <p>{{ oneroom.price }}</p>
  </div>
</template>

<script>
import onerooms from './data/oneroom.js';

export default {
  name: 'App',
  data() {
    return { 
      onerooms : onerooms,
      isModalOpened : false,
      prices : [60, 70, 80],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      menus : ['Home', 'Products', 'About'],
      target : undefined,
    }
  },
  methods : {
    increaseReport(i) {
      this.신고수s[i]++;
    },
    openModal(i) {
      this.target = onerooms[i];
      this.isModalOpened = true;
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width : 100%;
  margin-top: 40px;
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
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
.right-align {
  float: right;
}
</style>
