<template>
  <div class="category-navigation-container">
    <div class="category-navigation-navigation-bar">
      <button class="category-navigation-tab-button all-category">
        전체 카테고리
        <img src="../assets/dropdown_icon.svg" />
      </button>
      <button class="category-navigation-tab-button event">7월 가입혜택</button>
      <button
        v-for="data in navigationBoldData"
        :key="data"
        class="category-navigation-tab-button"
      >
        {{ data }}
      </button>
      <div class="category-navigation-line" />
      <div class="category-navigation-divider" />
      <button
        v-for="data in navigationNormalData"
        :key="data"
        class="category-navigation-tab-button normal-font"
      >
        {{ data }}
      </button>
      <button class="category-navigation-tab-button normal-font">
        Created by
        <div class="category-navigation-new-badge" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      navigationBoldData: ['바로수강', '얼리버드', '오픈 예정', '이벤트'],
      navigationNormalData: ['시그니처', '키즈'],
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
  width: 100%;
  background-color: rgb(255, 255, 255);
  z-index: 0;

  .category-navigation-navigation-bar {
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
      position: relative;
      box-sizing: border-box;
      border: none;
      outline: none;
      background-color: white;
      color: rgb(26, 26, 26);
      font-weight: bold;
      cursor: pointer;

      .category-navigation-new-badge {
        margin-left: 6px;
        width: 4px;
        height: 4px;
        border-radius: 2px;
        background: rgb(243, 33, 59);
      }
    }

    .category-navigation-tab-button:hover{
      font-weight: bold;
    }

    .category-navigation-tab-button.event:hover:after {
      background-color: rgb(29, 78, 250);
    }

    .category-navigation-tab-button:hover:after {
      content: '';
      background-color: rgb(26, 26, 26);
      position: absolute;
      bottom: 10px;
      left: 0px;
      width: 100%;
      height: 2px;
      z-index: 999;
    }

    .normal-font {
      font-weight: 400;
    }

    .event {
      color: rgb(29, 78, 250);
    }

    .category-navigation-line {
      min-height: 30px;
      width: 1px;
      background-color: rgb(248, 248, 248);
      margin-bottom: 12px;
    }

    .category-navigation-divider {
      margin-top: 14px;
      flex: 1 1 0%;
      max-width: 32px;
      height: 22px;
    }
  }
}
</style>
