<template>
  <div class="banner-wrapper">
    <div class="banner-fragnmnt-container">
      <div class="background-blurred-image-container">
        <img src="" alt="" class="background-blurred-image">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Banner',
  data() {
    return {
      dummyData: [
        {
          title: '오늘까지만 83% 할인!\n2021 여름감사제',
          description: '전 품목 최대 할인에\niPad Pro 자동 응모!',
          color: 'rgb(78, 98, 237)',
          image: 'banner1.png',
        },
        {
          title: '회원가입하\n쿠폰팩 선착순 증정!',
          description: '오직 7월 신규 회원을 위한\n특별 선물 증정!',
          color: 'rgb(255, 184, 0)',
          image: 'banner2.png',
        },
        {
          title: '이번 주 마감!\n최신형 아이맥의 주인공은?',
          description:
            '듣고 싶은 클래스를 댓글로 남기면\n최신형 아이맥 자동 응모!',
          color: 'rgb(244, 97, 105)',
          image: 'banner3.png',
        }
      ]
    }
  }
}
</script>

<style lang="scss">
.banner-wrapper {
  margin-bottom: 32px;

  .banner-fragnmnt-container {
    display: block;
    position: relative;
    width: 100%;
  }

}
</style>