<template>
  <div class="main">
    <Header />
    <Banner />
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import Banner from '../components/Banner.vue'

export default {
  name: 'Main',
  components: {
    Header: Header,
    Banner: Banner,
  },
}
</script>
