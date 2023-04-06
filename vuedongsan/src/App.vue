<template>
  <Modal :원룸들="원룸들" :눌렀니="눌렀니" :모달열렸니="모달열렸니" />
  <nav>
    <a href="" v-for="(a, i) in menuList" :key="i">{{ a }}</a>
  </nav>

  <DiscountBanner />
  <Card :원룸들="원룸들" />
  <!--
  <div v-for="b in products" :key="b">
    <h4 :style="titleColor">{{ b }}</h4>
    <span>xx만원</span>
  </div> -->

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
  <!-- 컴포넌트 사용법
  01. vue파일 import 해오고
  02. component:{} 에 등록하고
  03. 쓰셈
  
  - 컴포넌트 필요한 이유?
  01. 넘 긴 코드 이쁘게 보일라공
  02. 재사용
  03. 한번만 수정하면 되지라
  04. 반복적으로 쓰는것만 만들장 -->

  <!-- 자식C가 부모C의 데이터를 갖고싶으면 props
  01. 데이터 전송
  02. 데이터 등록
  03. 데이터 쓰셈
  
  01.<자식C :데이터이름 = "데이터"/>
  v-bind: 와 같음
  02.자식C 스크립트 영역에 props:{데이터이름 : 자료형이름}
  -->
</template>

<script>
import Modal from './Modal.vue';
import Card from './Card.vue';

import DiscountBanner from './DiscountBanner.vue';
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
  components: {
    Modal,
    Card,
    DiscountBanner,
  },
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
