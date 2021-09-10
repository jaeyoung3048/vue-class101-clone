<template>
  <div class="banner-wrapper">
    <div class="banner-fragment-container">
      <div class="banner-transition-container">
        <ul class="image-transition-wrapper" ref="imageContainer">
          <li
            class="swiper-image"
            v-for="item in dummyData"
            :key="item.title"
            ref="imageWrapper"
          >
            <img :src="item.image" />
          </li>
        </ul>
      </div>
    </div>
    <div class="banner-elements-fragment-container">
      <button @click="backSwipe()">이전으로</button>
      <button @click="nextSwipe()">다음으로</button>
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
          image: require('@/assets/banner/image1.png'),
        },
        {
          title: '회원가입하\n쿠폰팩 선착순 증정!',
          description: '오직 7월 신규 회원을 위한\n특별 선물 증정!',
          color: 'rgb(255, 184, 0)',
          image: require('@/assets/banner/image2.png'),
        },
        {
          title: '이번 주 마감!\n최신형 아이맥의 주인공은?',
          description:
            '듣고 싶은 클래스를 댓글로 남기면\n최신형 아이맥 자동 응모!',
          color: 'rgb(244, 97, 105)',
          image: require('@/assets/banner/image3.png'),
        }
      ],
      imageIndex: 0,
      // swipeLocation: 0,
    }
  },
  methods: {
    nextSwipe() {
      if (this.imageIndex == this.$refs.imageWrapper.length - 1) {
        this.imageIndex = 0
        this.translateImageContainer(0)
        return
      }
      this.imageIndex++
      this.translateImageContainer(this.getSwipeWidth() * -1)
    },
    translateImageContainer(width) {
      this.$refs.imageContainer.style.transform = `translateX(${width}px)`
      // this.swipeLocation = width
    },
    getSwipeWidth() {
      const imageWidth = this.$refs.imageWrapper[this.imageIndex].offsetWidth
      const swipeWidth = imageWidth * this.imageIndex
      return swipeWidth
    },
    backSwipe() {
      if (this.imageIndex == 0) {
        this.imageIndex = this.$refs.imageWrapper.length - 1
        this.translateImageContainer(this.getSwipeWidth() * -1)
        return
      }

      // this.translateImageContainer(
      //   this.swipeLocation +
      //     this.$refs.imageWrapper[this.imageIndex].offsetWidth
      // )
      this.imageIndex--
      this.translateImageContainer(this.getSwipeWidth() * -1)
    },
  },
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}
.banner-wrapper {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  margin: 0 auto 32px;

  .banner-fragment-container {
    position: relative;
    max-width: 660px;
    overflow: hidden;

    .image-transition-wrapper {
      display: flex;
      transition-duration: 0.5s;

      .swiper-image {
        padding-right: 16px;

        img {
          width: 660px;
        }
      }
    }
  }
}
</style>