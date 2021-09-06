<template>
  <div class="main">
    <Header />
    <Navbar />
    <Banner />
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import Navbar from '../components/Navbar.vue'
import Banner from '../components/Banner.vue'

export default {
  name: 'Main',
  components: {
    Header: Header,
    Banner: Banner,
    Navbar: Navbar,
  },
}
</script>
