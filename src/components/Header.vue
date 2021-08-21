<template>
  <div class="header-wrapper">
    <div class="header-box">
      <span class="logo-wrapper" :class="{ active: isShowCategory }">
        <a href="/">
          <img src="../assets/CLASS101_Logo.svg" alt="/" />
        </a>
      </span>
      <div class="search-input" :style="searchInputStyleHandler">
        <form class="search-container" :style="searchContainerStyleHandler">
          <input
            type="search"
            placeholder="찾으시는 취미가 있으신가요?"
            maxlength="100"
            @click="isShowController()"
          />
          <button class="search-button" :class="{ active: isShowCategory }">
            <img src="../assets/search_icon.svg" alt="/" />
          </button>
        </form>
        <button
          class="search-cancel-button"
          v-if="isShowCategory"
          @click="isShowController(true)"
        >
          취소
        </button>
      </div>
      <div class="cart-container" v-if="isShowCartText">
        <div class="cart-text-wrapper">
          <a href="/cart" class="cart-text">장바구니</a>
        </div>
      </div>
    </div>
    <div v-show="isShowCategory" class="search-container-wrapper">
      <div class="search-container">
        <div class="search-history-container">
          <div class="search-history-header">
            <h3 class="search-history-text">추천 검색어</h3>
          </div>
          <div class="recommend-search-keyword-list">
            <button
              class="candidate-item-button"
              v-for="recommended in dummyData.recommended"
              :key="recommended"
            >
              <div class="candidate-text">{{ recommended }}</div>
            </button>
          </div>
          <div class="divider-container">
            <hr color="#f8f8f8" class="divider-line" />
          </div>
          <div class="search-history-header-row">
            <h3 class="search-history-text">
              인기 검색어
              <div class="search-history-generated-at-container">
                <img src="../assets/Time_icon.svg" />
                <div class="search-history-generated-at-text">13:15 기준</div>
              </div>
            </h3>
          </div>
          <div class="popular-search-keyword-list-row">
            <div class="popular-search-keyword-list-column">
              <div
                class="candidate-item-container"
                v-for="(Item, index) in dummyData.popular.slice(-5)"
                :key="dummyData.popular[index]"
              >
                <span class="cadidate-item-number" v-if="index < 5">{{
                  index + 1
                }}</span>
                <span class="candidate-item-text" v-if="index < 5">{{
                  Item
                }}</span>
              </div>
            </div>
            <div class="popular-search-keyword-list-column">
              <div
                class="candidate-item-container"
                v-for="(Item, index) in dummyData.popular.slice(5)"
                :key="dummyData.popular[index]"
              >
                <span class="cadidate-item-number">{{ index + 6 }}</span>
                <span class="candidate-item-text">{{ Item }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      isShowCategory: false,
      isShowCartText: true,
      dummyData: {
        recommended: [
          '오늘의 특가',
          '아이패드0원',
          'TOP20',
          '1+1클래스',
          '여름 취미 추천',
          '감사제 특가',
          '10만원할인',
        ],
        popular: [
          '아이패드',
          '일러스트',
          '이모티콘',
          '드로잉',
          '포토샵',
          '뜨개질',
          '레진',
          '주식',
          '포토크리에이트',
          '가전주부 PICK',
        ],
      },
    }
  },
  computed: {
    searchInputStyleHandler() {
      if (this.isShowCategory) {
        return {
          width: '676px',
          margin: 'auto',
          'align-items': 'center',
        }
      } else {
        return {
          width: '420px',
        }
      }
    },
    searchContainerStyleHandler() {
      if (this.isShowCategory) {
        document.body.style.cssText = `overflow: hidden;`
        return {
          display: 'flex',
          'flex-direction': 'row',
        }
      } else {
        return {
          position: 'realtive',
          flex: '1 1 0%',
        }
      }
    },
  },
  methods: {
    isShowController(cancel) {
      if (cancel) {
        this.isShowCategory = false
        this.isShowCartText = true
      } else {
        this.isShowCategory = true
        this.isShowCartText = false
      }
    },
  },
}
</script>

<style lang="scss">
input::-ms-clear,
input::-ms-reveal {
  display: none;
  width: 0;
  height: 0;
}

input::-webkit-search-decoration,
input::-webkit-search-cancel-button,
input::-webkit-search-results-button,
input::-webkit-search-results-decoration {
  display: none;
}

.header-wrapper {
  width: 100%;
  height: 86px;

  .header-box {
    display: flex;
    justify-content: center;
    width: 100%;
    height: 48px;
    padding: 20px 0px;
    font-size: 0px;
    margin: 0px auto;
    max-width: 1176px;
    position: relative;

    .logo-wrapper.active {
      position: absolute;
      left: 0%;
      height: 50%;
    }

    .logo-wrapper {
      display: flex;
      align-items: center;
      margin-right: 28px;
      height: 100%;

      img {
        display: flex;
        width: auto;
        height: 24px;
      }
    }

    .search-input {
      display: flex;
      width: 420px;

      .search-container {
        flex: 1 1 0%;
        align-items: center;

        input {
          display: flex;
          font-size: 14px;
          font-weight: normal;
          line-height: 20px;
          margin: 0px;
          width: 100%;
          padding: 12px 52px 12px 16px;
          background: rgb(248, 248, 249);
          border: 1px solid rgb(248, 248, 249);
          box-sizing: border-box;
          border-radius: 24px;
          text-align: left;
          color: rgb(26, 26, 26);
        }

        input:focus {
          outline: none;
        }

        .search-button.active {
          top: -3px;
          left: -8%;
        }

        .search-button {
          cursor: pointer;
          outline: none;
          position: relative;
          top: calc(-50% - 12px);
          left: calc(100% - 48px);
          padding: 0px;
          width: 20px;
          height: 20px;
          background-color: rgb(248, 248, 249);
          border-color: rgb(248, 248, 249);
          border: none;
          margin: 0px;
          color: #ffffff;
          a {
            width: 20px;
            height: 20px;
          }
        }
      }
      .search-cancel-button {
        display: inline;
        font-size: 14px;
        line-height: 20px;
        letter-spacing: -0.15px;
        margin: 0px 0px 0px 16px;
        border: none;
        outline: none;
        padding: 0px;
        height: fit-content;
        background-color: transparent;
        cursor: pointer;
        text-decoration: none;
        font-weight: 500;
        color: rgb(162, 162, 162);
        white-space: nowrap;
      }
    }
    .cart-container {
      display: flex;
      align-items: center;
      margin-left: auto;
      position: relative;
      .cart-text-wrapper {
        display: flex;
        justify-content: flex-end;
        flex-grow: 1;
        .cart-text {
          position: relative;
          white-space: nowrap;
          color: inherit;
          text-decoration: none;
          font-size: 14px;
        }
      }
    }
  }
  .search-container-wrapper {
    background-color: rgb(255, 255, 255);
    .search-container {
      max-width: 676px;
      margin: auto;
      padding-bottom: 20px;
      .search-history-container {
        padding: 24px 0px 28px;
        width: 100%;
        border-radius: 0px 0px 3px 3px;
        .search-history-header {
          display: flex;
          align-items: center;
          margin-bottom: 12px;
          .search-history-text {
            display: flex;
            font-size: 14px;
            line-height: 20px;
            flex: 1 1 0%;
            margin: 0px;
          }
        }
        .recommend-search-keyword-list {
          display: flex;
          flex-wrap: wrap;
          padding-bottom: 8px;
          .candidate-item-button {
            background-color: rgb(248, 248, 248);
            border: 0px;
            margin: 8px 4px 0px 0px;
            padding: 8px 16px;
            cursor: pointer;
            border-radius: 30px;
          }
        }
        .divider-container {
          margin: 16px 0px 24px;
          .divider-line {
            border: none;
            height: 1px;
            margin: 0px !important;
          }
        }
        .search-history-header-row {
          display: flex;
          align-items: center;
          margin-bottom: 12px;
          .search-history-text {
            display: flex;
            font-size: 14px;
            line-height: 20px;
            flex: 1 1 0%;
            margin: 0px;
            .search-history-generated-at-container {
              display: flex;
              align-items: center;
              margin-left: 6px;
              img {
                width: 14px;
                height: 14px;
              }
              .search-history-generated-at-text {
                font-size: 11px;
                font-weight: normal;
                line-height: 16px;
                letter-spacing: normal;
                margin: 0px 0px 0px 4px;
                color: rgb(202, 202, 202);
              }
            }
          }
        }
        .popular-search-keyword-list-row {
          display: flex;
          .popular-search-keyword-list-column {
            max-width: 50%;
            flex: 1 0 50%;
            .candidate-item-container {
              padding: 8px 0px;
              font-size: 14px;
              line-height: 20px;
              .cadidate-item-number {
                width: 18px;
                margin-right: 8px;
                font-weight: bold;
                letter-spacing: -1px;
                color: rgb(255, 86, 0);
              }
              .candidate-item-text {
                margin-bottom: 0px;
                color: rgb(26, 26, 26);
              }
            }
          }
        }
      }
    }
  }
}
</style>
