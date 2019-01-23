<!-- 相框 -->
<template>
  <div class="container">
    <div
      class="bulm-wrap"
      :style="{'transform':'translateX(-'+offset+'px)'}"
    >
      <div
        v-for="(item,index) in picArr"
        :key="index"
        class="bulm"
      >
        <section>
          <div>
            <p>{{ item.t1 }}</p>
            <p>{{ item.t2 }}</p>
          </div>
          <img :src="item.src">
        </section>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      offset: 0,
      picArr: [
        {
          t1: '1',
          t2: 'des',
          src:
            'https://cdn.dribbble.com/users/60166/screenshots/5265791/eagle.jpg'
        },
        {
          t1: '2',
          t2: 'des',
          src:
            'https://cdn.dribbble.com/users/60166/screenshots/4928758/cake_logo.jpg'
        },
        {
          t1: '3',
          t2: 'des',
          src:
            'https://cdn.dribbble.com/users/60166/screenshots/4743479/kraken2.jpg'
        },
        {
          t1: '4',
          t2: 'des',
          src:
            'https://cdn.dribbble.com/users/60166/screenshots/5265791/eagle.jpg'
        },
        {
          t1: '5',
          t2: 'des',
          src:
            'https://cdn.dribbble.com/users/60166/screenshots/4928758/cake_logo.jpg'
        },
        {
          t1: '6',
          t2: 'des',
          src:
            'https://cdn.dribbble.com/users/60166/screenshots/4743479/kraken2.jpg'
        }
      ]
    }
  },
  mounted() {
    this.loop()
  },
  methods: {
    loop() {
      setInterval(() => {
        if (this.offset < this.picArr.length * 340) {
          this.offset += 340
          this.picArr.push(this.picArr[0])
          this.picArr.splice(0, 1)
          this.offset = 0
        } else {
          this.offset = 0
        }
      }, 3000)
    }
  }
}
</script>

<style lang='less' scoped>
.container {
  position: relative;
  overflow: hidden;
  z-index: 10;
}
.bulm-wrap {
  transition: transform 0.25s linear;
  display: flex;
  padding-bottom: 20px;
  .bulm {
    margin: 0 60px;
    section {
      width: 220px;
      height: 300px;
      background: rgba(255, 255, 255, 0.9);
      position: relative;
      box-shadow: 0 2px 5px #dcdcdc;
      div {
        padding-top: 30px;
        font-weight: 300;
        p {
          display: block;
          text-align: center;
        }
        p:first-child {
          font-size: 36px;
        }
        p:last-child {
          font-size: 18px;
        }
      }
      img {
        position: absolute;
        bottom: 0;
        z-index: -10;
        width: 100%;
        height: 50%;
      }
    }
  }
}
</style>
