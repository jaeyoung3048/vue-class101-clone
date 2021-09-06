<template>
  <div class="category-navigation-container">
    <div class="category-navigation-navigation-bar">
      <button
        class="category-navigation-tab-button all-category"
        @click="isShowAllCategoryHandler()"
      >
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
    <div
      class="category-navigation-categories-wrapper"
      v-if="isShowAllCategory"
    >
      <section class="top-categories-group-wrapper">
        <section class="top-categories-group first-categories-group">
          <section class="top-categories-group root-category-group">
            <h2>크리에이티브</h2>
            <h3
              v-for="data in Object.keys(dummyData)"
              :key="data"
              class="top-categories-group child-category-label"
              @mouseover="isShowSecondCategoryHandler()"
            >
              {{ data }}
            </h3>
          </section>
        </section>
        <section
          class="top-categories-group second-categories-group"
          v-if="isShowSecondCategory"
        >
          <section class="top-categories-group root-category-group">
            <h2>크리에이티브</h2>
            <h3
              v-for="(data, key, index) in dummyData"
              :key="index"
              class="top-categories-group child-category-label"
            >
              {{ key }}
            </h3>
          </section>
        </section>
      </section>
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
      selectedCategory: '',
      isShowAllCategory: false,
      isShowSecondCategory: false,
    }
  },
  methods: {
    isShowAllCategoryHandler() {
      this.isShowAllCategory = !this.isShowAllCategory
    },
    secondCategoryHandler() {
      this.isShowSecondCategory = !this.isShowSecondCategory

    },
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

  .category-navigation-categories-wrapper {
    position: absolute;
    background-color: rgb(255, 255, 255);
    display: flex;
    margin-left: 352px;
    top: 52px;
    border-right: 1px solid rgb(239, 239, 239);
    border-bottom: 1px solid rgb(239, 239, 239);
    border-left: 1px solid rgb(239, 239, 239);
    border-image: initial;
    border-top: none;
    z-index: 51;

    .top-categories-group-wrapper {
      display: flex;
      flex-direction: row;
      border-radius: 2px;

      .top-categories-group.first-categories-group {
        width: 220px;
        overflow: auto;
        margin-top: 20px;
        padding: 0px 12px;

        .top-categories-group.root-category-group {
          margin: 0px;
          padding-bottom: 20px;

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

          h3 {
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

        .top-categories-group.root-category-group {
          margin: 0px;
          padding-bottom: 20px;

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

          h3 {
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
