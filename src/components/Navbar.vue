<template>
  <div class="category-navigation-container">
    <div class="category-navigation-navigation-bar">
      <all-category-btn />
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
import AllCategoryBtn from './AllCategoryBtn.vue'

export default {
  name: 'Navbar',
  components: {
    'all-category-btn': AllCategoryBtn,
  },
  data() {
    return {
      navigationBoldData: ['바로수강', '얼리버드', '오픈 예정', '이벤트'],
      navigationNormalData: ['시그니처', '키즈'],
      selectedCategory: '',
    }
  },
}
</script>

<style lang="scss">
.category-navigation-container {
  position: relative;
  width: 100%;
  background-color: rgb(255, 255, 255);
  z-index: 1;

  .category-navigation-navigation-bar {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    width: 100%;
    max-width: 1176px;
    margin: 0px auto;
    background-color: rgb(255, 255, 255);
    overflow: auto;

    .category-navigation-tab-button {
      display: flex;
      position: relative;
      line-height: 24px;
      padding: 8px 0px 20px;
      border: none;
      outline: none;
      margin-right: 28px;
      box-sizing: border-box;
      background-color: white;
      color: rgb(26, 26, 26);
      font: {
        size: 16px;
        weight: 700;
      }
      cursor: pointer;

      .category-navigation-new-badge {
        margin-left: 6px;
        width: 4px;
        height: 4px;
        border-radius: 2px;
        background: rgb(243, 33, 59);
      }
    }

    .category-navigation-tab-button:hover {
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

  .category-navigation-categories-wrapper {
    $border: 1px solid rgb(239, 239, 239);

    position: absolute;
    background-color: rgb(255, 255, 255);
    display: flex;
    margin-left: 352px;
    top: 52px;
    z-index: 51;
    border: {
      left: $border;
      right: $border;
      bottom: $border;
    }
    // border: 1px solid rgb(239, 239, 239);
    // border-top: none;

    .top-categories-group-wrapper {
      display: flex;
      flex-direction: row;
      border-radius: 2px;

      .top-categories-group.first-categories-group {
        width: 220px;
        overflow: auto;
        margin-top: 20px;
        padding: 0px 12px;

        h2 {
          padding-left: 20px;
          font-weight: bold;
          font-size: 11px;
          color: rgb(162, 162, 162);
          display: flex;
          -webkit-box-align: center;
          align-items: center;
          margin: 0px 0px 4px;
          line-height: unset;
        }

        .top-categories-group.root-category-group {
          margin: 0px;
          padding-bottom: 20px;
          list-style: none;
          padding: 0;

          li {
            list-style: none;
            padding: 8px 8px 8px 20px;
            font-size: 14px;
            line-height: 18px;
            margin: 0px;
            color: rgb(26, 26, 26);
            display: flex;
            -webkit-box-align: center;
            align-items: center;
            -webkit-box-pack: justify;
            justify-content: space-between;
            font-weight: normal;
            cursor: pointer;
          }
        }
      }

      .top-categories-group.second-categories-group {
        width: 220px;
        overflow: auto;
        margin-top: 20px;
        padding: 0px 12px;

        h2 {
          padding-left: 20px;
          font-weight: bold;
          font-size: 11px;
          color: rgb(162, 162, 162);
          display: flex;
          -webkit-box-align: center;
          align-items: center;
          margin: 0px 0px 4px;
          line-height: unset;
        }

        .top-categories-group.root-category-group {
          margin: 0px;
          padding-bottom: 20px;
          list-style: none;
          margin: 0;

          li {
            list-style: none;
            padding: 8px 8px 8px 20px;
            font-size: 14px;
            line-height: 18px;
            margin: 0px;
            color: rgb(26, 26, 26);
            display: flex;
            -webkit-box-align: center;
            align-items: center;
            -webkit-box-pack: justify;
            justify-content: space-between;
            font-weight: normal;
            cursor: pointer;
          }
        }
      }

      .second-categories-group {
        border-left: 1px solid rgb(239, 239, 239);
        width: 220px;
        padding: 0px 12px;
        margin-top: 20px;
      }
    }
  }
}
</style>
