<template>
<div class="black-bg" v-if="모달창열렸니 == true">
  <div class="white-bg">
    <img :src="원룸들[누른거].image" alt="" class="room-img">
    <h4>{{원룸들[누른거].title}}</h4>
    <p>{{원룸들[누른거].content}}</p>
    <button @click="모달창열렸니 = false">닫기</button>
  </div>
</div>

<div class="menu">
    <a v-for="작명 in 메뉴들" :key="작명">{{ 작명 }}</a>
  </div>
  

  <div v-for="(작명,i) in 원룸들" :key="i">
    <img :src="작명.image" alt="" class="room-img" />
    <h3 @click="모달창열렸니 = true; 누른거 = i">{{작명.title}}</h3>
    <p>{{작명.price}}원</p>
  </div>

</template>

<script>
import data from './assets/oneroom.js';


export default {
  name: "App",
  data() {
    return {
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수: [0, 0, 0],
      메뉴들: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase() {
      this.신고수++;
    },
  },
  components: {},
};
</script>

<style>
body{
  margin : 0
}
div{
  box-sizing: border-box;
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
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img{
  width:100%;
  margin-top: 40px;
}
</style>
