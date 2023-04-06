<template>
  <div v-for="(작명, i) in 원룸들" :key="i">
    <img :src="작명.image" />
    <h4
      @click="
        모달열렸니 = true;
        눌렀니 = i;
      "
      :style="titleColor"
    >
      {{ 작명.title }}
    </h4>
    <span>{{ 작명.price }}원</span>
    <!-- <div>
      <button @click="신고수[0]++">허위매물신고</button>
      <span>신고 수 : {{ 신고수[0] }} </span>
    </div> -->
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    원룸들: Array,
  },
};
</script>

<style></style>
