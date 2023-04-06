<template>
  <div class="black-bg" v-if="모달열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[눌렀니].image" :alt="원룸들[눌렀니].title + `이미지`" />
      <h4>{{ 원룸들[눌렀니].title }}</h4>
      <p>{{ 원룸들[눌렀니].content }}</p>
      <strong style="display: block">{{ 원룸들[눌렀니].price }}</strong>
      <button @click="모달열렸니 = false">닫기</button>
    </div>
  </div>

  <nav>
    <a href="" v-for="(a, i) in menuList" :key="i">{{ a }}</a>
  </nav>
  <!--
  <div v-for="b in products" :key="b">
    <h4 :style="titleColor">{{ b }}</h4>
    <span>xx만원</span>
  </div> -->
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

  <!-- :속성 = "데이터이름"  /  내용에 데이터 바인딩 {{ 데이터 }}-->
  <!-- vue 반복문 / v-for="작명 in 몇회 반복할지" :key="작명" or v-for="(작명,i) in 몇회 반복할지" :key="i"  -->
  <!-- 이벤트 핸들러 / v-on:click="" / @click="" / @mouseover : hover 등.  -->
  <!-- 동적 UI만드는 법 
    00. 디자인하기
    01. UI의 현재 상태를 데이터로 저장해둠 ex)모달열렸니: false,
    02. 데이터에 따라 UI가 어떻게 보일지 작성 ex) @click="모달열렸니 = true"
  -->
  <!-- export default 파일명 / import 파일명 from '경로'-->
  <!-- export {변수 , 변수2, 함수1, 함수2} / import {변수} from '경로'-->
  <!-- v-if 가 참이 아니면 v-else / v-else-if="1==3"-->
</template>

<script>
import postData from './assets/post';
export default {
  name: 'App',
  data() {
    return {
      titleColor: 'color:blue',
      menuList: ['Home', 'about', 'shop'],
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      신고수: [0, 0, 0],
      모달열렸니: false,
      눌렀니: 0,
      원룸들: postData,
    };
  },
  methods: {
    increase() {
      this.신고수 += 1;
      // 신고수 ++; <- error.
      //data return 안에 있는걸 들고 오고싶을땐 this.OOO 으로 사용 가능.
    },
  },
  components: {},
  mounted: function () {
    console.log('mounted', postData);
    //this.message = "Do Update";
  },
};
</script>

<style>
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
}
.white-bg {
  width: 100%;
  background: #fff;
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

nav {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
nav a {
  color: white;
  padding: 10px;
}
/* 
button {
  display: block;
  margin: 0 auto;
} */

img {
  width: 100%;
}
</style>
