<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" alt="" class="room-img" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <input v-model.number="month"/>
      <p>{{month}} X 개월 선택함 : {{ 원룸들[누른거].price*month }}원</p>
      <!-- <button @click="모달창열렸니 = false">닫기</button> -->
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  //eslint-disable-next-line
  name: "Modal",
  data() {
    return {
      month: 1,
    };
  },
  watch:{
    month(a){
      if( a >= 13){
        alert('12개월 까지만 가능합니다.');
        this.month = 1;
      }else if(isNaN(a)){
        alert('숫자만 입력가능합니다.')  
        this.month = "";
      }
    },
  },
  props: {
    원룸들: Array,
    누른거: Number,
    모달창열렸니: Boolean,
  },
};
</script>

<style>
</style>