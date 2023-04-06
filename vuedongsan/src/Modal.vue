<template>
  <div class="black-bg" v-if="모달열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[눌렀니].image" :alt="원룸들[눌렀니].title + `이미지`" />
      <h4>{{ 원룸들[눌렀니].title }}</h4>
      <p>{{ 원룸들[눌렀니].content }}</p>
      <strong style="display: block">{{ 원룸들[눌렀니].price }}</strong>
      <DiscountBanner />
      <!-- <button @click="모달열렸니 = false">닫기</button> -->
      <!-- // props는 read-only라서 받아온거 수정X -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    원룸들: Array, //받아온 자료
    눌렀니: Number,
    모달열렸니: Boolean,
  },
};
</script>

<style>
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
}
.white-bg {
  width: 100%;
  background: #fff;
  border-radius: 8px;
  padding: 20px;
}
</style>
