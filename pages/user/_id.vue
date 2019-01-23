<!--  -->
<template>
  <div>用户id页</div>
</template>
<script>
export default {
  data() {
    return {
      id: '0'
    }
  },
  validate({ params }) {
    return /^\d+$/.test(params.id)
  }
}
</script>
