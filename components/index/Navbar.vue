<!--  -->
<template>
  <div class="navbar">
    <div class="hitokoto">
      {{ hitokoto }}
    </div>
    <div class="widget">
      <router-link to="/">
        <img class="home" :src="homeImgSrc" @mouseover="handleHomeHover" @mouseout="handleHomeLeave">
      </router-link>
    </div>
  </div>
</template>

<script>
import homeDefault from '@/assets/img/home.png'
import homeActive from '@/assets/img/home-active.png'
export default {
  data() {
    return {
      hitokoto: '一言蓄力中……',
      homeImgSrc: homeDefault
    }
  },
  mounted() {
    this.getHitokoto()
  },
  methods: {
    handleHomeHover() {
      this.homeImgSrc = homeActive
    },
    handleHomeLeave() {
      this.homeImgSrc = homeDefault
    },
    getHitokoto() {
      setInterval(() => {
        this.$axios.get(`https://v1.hitokoto.cn/?encode=json`).then(res => {
          this.hitokoto = res.data.hitokoto
        })
      }, 5000)
    }
  }
}
</script>

<style lang='less' scoped>
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 14px;
  padding: 10px 0;
  border-bottom: 1px solid #eaeaea;
  .hitokoto {
    font-weight: 300;
    color: #333;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    flex: 1;
  }
  .widget {
    .home {
      vertical-align: middle;
      width: 16px;
      height: 16px;
    }
    .home:hover {
      cursor: pointer;
    }
  }
}
</style>
