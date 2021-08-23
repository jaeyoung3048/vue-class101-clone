<template>
  <div class="category-navigation-container">
    <div class="category-navigation-navigation-bar">
      <button class="category-navigation-tab-button all-category">
        전체 카테고리
        <img src="../assets/dropdown_icon.svg" />
      </button>
      <button class="category-navigation-tab-button event">7월 가입혜택</button>
      <button
        v-for="data in navigationData"
        :key="data"
        class="category-navigation-tab-button"
      >
        {{ data }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      navigationData: ['바로수강', '얼리버드', '오픈 예정', '이벤트'],
      dummyData: {
        드로잉: ['펜, 연필', '마카', '색연필'],
        공예: ['실 공예', '대바늘뜨개', '실바늘뜨개'],
        '요리, 음료': ['아시안', '양식', '중식'],
      },
    }
  },
}
</script>

<style lang="scss">
.category-navigation-container {
  position: relative;
  width: 100%;
  background-color: rgb(255, 255, 255);
  .category-navigation-navigation-bar {
    position: relative;
    width: 100%;
    max-width: 1176px;
    margin: 0px auto;
    background-color: rgb(255, 255, 255);
    display: flex;
    align-items: center;
    overflow: auto;
    justify-content: flex-start;
    .category-navigation-tab-button {
      font-size: 16px;
      line-height: 24px;
      margin-right: 28px;
      padding: 8px 0px 20px;
      display: flex;
      box-sizing: border-box;
      border: none;
      outline: none;
      background-color: white;
      color: rgb(26, 26, 26);
      font-weight: bold;
      cursor: pointer;
    }
    .event {
      color: rgb(29, 78, 250);
    }
  }
}
</style>
