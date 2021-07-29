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
  </div>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style lang="scss">
.HeaderWrapper {
  display: flex;
  justify-content: center;
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
        .SearchInput__SearchButton {
          cursor: pointer;
          outline: none;
          position: relative;
          top: calc(-50% - 10px);
          right: -40%;
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
}
</style>
