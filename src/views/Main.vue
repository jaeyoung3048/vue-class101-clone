<template>
  <div class="main">
    <main-header />
  </div>
</template>

<script>
import Header from '../components/Header.vue'

export default {
  name: 'Main',
  components: {
    'main-header': Header,
  },
}
</script>
