<template>
  <div class="HeaderWrapper">
    <div class="HeaderBox">
      <span class="LogoWrapper" v-bind:class="isShowCategory ? 'Active' : ''">
        <a href="/">
          <img src="../assets/CLASS101_Logo.svg" alt="/" />
        </a>
      </span>
      <div class="SearchInput" v-bind:style="SearchInputHandler">
        <form class="SearchContainer" v-bind:style="SearchContainerHandler">
          <input
            type="search"
            placeholder="찾으시는 취미가 있으신가요?"
            maxlength="100"
            v-on:click="
              isShowCategory = true
              isShowCartText = false
            "
          />
          <button
            class="SearchInput__SearchButton"
            v-bind:class="isShowCategory ? 'Active' : ''"
          >
            <img src="../assets/search_icon.svg" alt="/" />
          </button>
        </form>
        <button
          class="Search__CancelButton"
          v-if="isShowCategory"
          v-on:click="
            isShowCategory = false
            isShowCartText = true
          "
        >
          취소
        </button>
      </div>
      <div class="CartContainer" v-if="isShowCartText">
        <div class="CartLink__Wrapper">
          <a href="/cart" class="CartLink">장바구니</a>
        </div>
      </div>
    </div>
    <div class="MainSearchContainer__Wrapper" v-show="isShowCategory">
      <div class="MainSearchContainer">
        <div class="SearchHistory__Container">
          <div class="SearchHistory__Header">
            <h3 class="SearchHistory__Text">추천 검색어</h3>
          </div>
          <div class="RecommendSearchKeywordList__Container">
            <button
              class="CandidateItem__Button"
              v-for="recommended in DummyData.recommended"
              :key="recommended"
            >
              <div class="CandidateText">{{ recommended }}</div>
            </button>
          </div>
          <div class="Divider__Container">
            <hr color="#f8f8f8" class="Divider__Line" />
          </div>
          <div class="SearchHistory__HeaderRow">
            <h3 class="SearchHistory__Text">
              인기 검색어
              <div class="SearchHistory__GeneratedAt">
                <img src="../assets/Time_icon.svg" />
                <div class="SearchHistory__GeneratedAtText">13:15 기준</div>
              </div>
            </h3>
          </div>
          <div class="PopularSearchKeywordList__Row">
            <div class="PopularSearchKeywordList__Column">
              <div
                class="CandidateItem__Container"
                v-for="(Item, index) in DummyData.popular.slice(-5)"
                :key="DummyData.popular[index]"
              >
                <span class="CadidateItem__Number" v-if="index < 5">{{
                  index + 1
                }}</span>
                <span class="CandidateItem__Text" v-if="index < 5">{{
                  Item
                }}</span>
              </div>
            </div>
            <div class="PopularSearchKeywordList__Column">
              <div
                class="CandidateItem__Container"
                v-for="(Item, index) in DummyData.popular.slice(5)"
                :key="DummyData.popular[index]"
              >
                <span class="CadidateItem__Number">{{ index + 6 }}</span>
                <span class="CandidateItem__Text">{{ Item }}</span>
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
  data: () => {
    return {
      isShowCategory: false,
      isShowCartText: true,
      DummyData: {
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
    SearchInputHandler: function() {
      if (this.isShowCategory == true) {
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
    SearchContainerHandler: function() {
      if (this.isShowCategory == true) {
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
}
</script>

<style lang="scss">
.HeaderWrapper {
  width: 100%;
  height: 5.375rem;
  .HeaderBox {
    display: flex;
    padding: 20px 0px;
    font-size: 0px;
    justify-content: center;
    height: 48px;
    width: 100%;
    margin: 0px 372px;
    max-width: 1176px;
    position: relative;
    .LogoWrapper.Active {
      position: absolute;
      left: 0%;
      height: 50%;
    }
    .LogoWrapper {
      display: flex;
      margin-right: 28px;
      height: 100%;
      align-items: center;
      img {
        display: flex;
        width: auto;
        height: 24px;
      }
    }
    .SearchInput {
      display: flex;
      width: 420px;
      form {
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
        .SearchInput__SearchButton.Active {
          top: -3px;
          left: -8%;
        }
        .SearchInput__SearchButton {
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
      .Search__CancelButton {
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
    .CartContainer {
      display: flex;
      align-items: center;
      margin-left: auto;
      position: relative;
      .CartLink__Wrapper {
        display: flex;
        justify-content: flex-end;
        flex-grow: 1;
        .CartLink {
          position: relative;
          white-space: nowrap;
          color: inherit;
          text-decoration: none;
          font-size: 14px;
        }
      }
    }
  }
  .MainSearchContainer__Wrapper {
    background-color: rgb(255, 255, 255);
    .MainSearchContainer {
      max-width: 676px;
      margin: auto;
      padding-bottom: 20px;
      .SearchHistory__Container {
        padding: 24px 0px 28px;
        width: 100%;
        border-radius: 0px 0px 3px 3px;
        .SearchHistory__Header {
          display: flex;
          align-items: center;
          margin-bottom: 12px;
          .SearchHistory__Text {
            display: flex;
            font-size: 14px;
            line-height: 20px;
            flex: 1 1 0%;
            margin: 0px;
          }
        }
        .RecommendSearchKeywordList__Container {
          display: flex;
          flex-wrap: wrap;
          padding-bottom: 8px;
          .CandidateItem__Button {
            background-color: rgb(248, 248, 248);
            border: 0px;
            margin: 8px 4px 0px 0px;
            padding: 8px 16px;
            cursor: pointer;
            border-radius: 30px;
          }
        }
        .Divider__Container {
          margin: 16px 0px 24px;
          .Divider__Line {
            border: none;
            height: 1px;
            margin: 0px !important;
          }
        }
        .SearchHistory__HeaderRow {
          display: flex;
          align-items: center;
          margin-bottom: 12px;
          .SearchHistory__Text {
            display: flex;
            font-size: 14px;
            line-height: 20px;
            flex: 1 1 0%;
            margin: 0px;
            .SearchHistory__GeneratedAt {
              display: flex;
              align-items: center;
              margin-left: 6px;
              img {
                width: 14px;
                height: 14px;
              }
              .SearchHistory__GeneratedAtText {
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
        .PopularSearchKeywordList__Row {
          display: flex;
          .PopularSearchKeywordList__Column {
            max-width: 50%;
            flex: 1 0 50%;
            .CandidateItem__Container {
              padding: 8px 0px;
              font-size: 14px;
              line-height: 20px;
              .CadidateItem__Number {
                width: 18px;
                margin-right: 8px;
                font-weight: bold;
                letter-spacing: -1px;
                color: rgb(255, 86, 0);
              }
              .CadidateItem__Text {
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
