<template>
  <div>
    <img :src="원룸들.image" alt="" class="room-img" />
    <h3 @click="$emit('openModal', 원룸들.id)">
      {{ 원룸들.title }}
    </h3>
    <p>{{ 원룸들.content }}원</p>
    <p>{{ 원룸들.price }}원</p>
  </div>
</template>

<script>
export default {
  //eslint-disable-next-line
  name: "Card",
  props: {
    원룸들: Object,
  },
};
</script>

<style>
</style>