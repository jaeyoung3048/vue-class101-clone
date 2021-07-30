<template>
  <div class="HeaderWrapper">
    <div class="HeaderBox">
      <span class="LogoWrapper">
        <a href="/">
          <img src="../assets/CLASS101_Logo.svg" alt="/" />
        </a>
      </span>
      <div class="SearchInput">
        <form class="SearchContainer">
          <input
            type="search"
            placeholder="찾으시는 취미가 있으신가요?"
            maxlength="100"
          />
          <button class="SearchInput__SearchButton">
            <img src="../assets/search_icon.svg" alt="/" />
          </button>
        </form>
      </div>
      <div class="CartContainer">
        <div class="CartLink__Wrapper">
          <a href="/cart" class="CartLink">장바구니</a>
        </div>
      </div>
    </div>
    <div class="MainSearchContainer__Wrapper">
      <div class="MainSearchContainer">
        <div class="SearchHistory__Container">
          <div class="SearchHistory__Header">
            <h3 class="SearchHistory__Text">추천 검색어</h3>
          </div>
          <div class="RecommendSearchKeywordList__Container">
            <button class="CandidateItem__Button">
              <div class="CandidateText">오늘만 특가</div>
            </button>
            <button class="CandidateItem__Button">
              <div class="CandidateText">아이패드0원</div>
            </button>
            <button class="CandidateItem__Button">
              <div class="CandidateText">TOP20</div>
            </button>
            <button class="CandidateItem__Button">
              <div class="CandidateText">1+1클래스</div>
            </button>
            <button class="CandidateItem__Button">
              <div class="CandidateText">여름 취미 추천</div>
            </button>
            <button class="CandidateItem__Button">
              <div class="CandidateText">감사제 특가</div>
            </button>
            <button class="CandidateItem__Button">
              <div class="CandidateText">10만원할인</div>
            </button>
          </div>
          <div class="Divider__Container">
            <hr color="#f8f8f8" class="Divider__Line" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import DummyData from '../../data.json'

export default {
  name: 'Header',
  data() {
    return {
      isShowCategory: false,
    }
  },
  methods: {
    isShowCategoryController: () => {
      this.isShowCategory
        ? this.isShowCategory == false
        : this.isShowCategory == true
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
        position: realtive;
        flex: 1 1 0%;
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
        .SearchInput__SearchButton {
          cursor: pointer;
          outline: none;
          position: relative;
          top: calc(-50% - 12px);
          left: 85%;
          padding: 0px;
          width: 20px;
          height: 20px;
          background-color: rgb(248, 248, 249);
          border-color: rgb(248, 248, 249);
          border: none;
          color: #ffffff;
          a {
            width: 20px;
            height: 20px;
          }
        }
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
      }
    }
  }
}
</style>
