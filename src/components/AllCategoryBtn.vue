<template>
  <div class="">
    <button
      class="category-navigation-tab-button all-category"
      @click="toggleIsShowAllCategory()"
    >
      전체 카테고리
      <img src="../assets/dropdown_icon.svg" />
    </button>
    <div
      class="category-navigation-categories-wrapper"
      v-if="isShowAllCategory"
    >
      <section class="top-categories-group-wrapper">
        <section class="top-categories-group first-categories-group">
          <h2>크리에이티브</h2>
          <ul class="top-categories-group root-category-group">
            <li
              v-for="data in Object.keys(dummyData)"
              :key="data"
              class="top-categories-group child-category-label"
              @mouseover="toggleIsShowSecondCategory()"
              @mouseout="toggleIsShowSecondCategory()"
            >
              {{ data }}
            </li>
          </ul>
        </section>
        <section
          class="top-categories-group second-categories-group"
          v-if="isShowSecondCategory"
        >
          <h2>크리에이티브</h2>
          <ul class="top-categories-group root-category-group">
            <li
              v-for="(data, key) in dummyData"
              :key="key"
              class="top-categories-group child-category-label"
            >
              {{ key }}
            </li>
          </ul>
        </section>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AllCategoryBtn',
  data() {
    return {
      isShowAllCategory: false,
      isShowSecondCategory: false,
      dummyData: {
        드로잉: ['펜, 연필', '마카', '색연필'],
        공예: ['실 공예', '대바늘뜨개', '실바늘뜨개'],
        '요리, 음료': ['아시안', '양식', '중식'],
      },
    }
  },
  methods: {
    // method 명은 동사로 시작한다.
    toggleIsShowAllCategory() {
      this.isShowAllCategory = !this.isShowAllCategory
    },
    toggleIsShowSecondCategory() {
      this.isShowSecondCategory = !this.isShowSecondCategory
    },
  },
}
</script>

<style></style>
