<template>
  <transition name="fade">
    <Modal
      @closeModal="모달창열렸니 = false"
      v-bind:원룸들="원룸들"
      v-bind:누른거="누른거"
      v-bind:모달창열렸니="모달창열렸니"
    />
  </transition>
  <div class="menu">
    <a v-for="작명 in 메뉴들" :key="작명">{{ 작명 }}</a>
  </div>

  <Discount v-if="showDiscount == true"></Discount>

  <button @click="priceSort">가격순정렬</button>
  <button @click="resetSort">리셋</button>

  <Card
    @openModal="
      모달창열렸니 = true;
      누른거 = $event;
    "
    v-bind:원룸들="원룸들[i]"
    v-for="(작명, i) in 원룸들"
    :key="작명"
  />
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
      원룸들오리지널: [...data],
      누른거: 0,
      원룸들: data,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      메뉴들: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase() {
      this.신고수++;
    },
    priceSort() {
      this.원룸들.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    resetSort() {
      this.원룸들 = [...this.원룸들오리지널];
    },
  },
  mounted() {
    setTimeout(() =>{
      this.showDiscount = false;
    }, 2000);
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
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
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

div {
  box-sizing: border-box;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
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
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
