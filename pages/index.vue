<template>
  <div id="app">
    <div class="m1024 mb30">
      <Navbar />
    </div>
    <div class="m1024 mb30">
      <Bulm />
    </div>
  </div>
</template>

<script>
import Bulm from '@/components/index/Bulm'
import Navbar from '@/components/index/Navbar'

export default {
  components: {
    Bulm,
    Navbar
  }
}
</script>

<style lang="less" scoped>
#app {
  height: 100%;
}
</style>
