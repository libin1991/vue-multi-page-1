<template>
  <div>
    <!-- <img :src="loadingImg" alt=""> -->
    <div class="img-box" v-for="(item, index) in imgList" :key="index">
      <!-- <img :src="item" loading="lazy" alt="demo"> -->
      <img class="lazy-image" v-imgLazy="item" alt="..." />
      <!-- <iframe :src="item" loading="lazy"></iframe> -->
    </div>
  </div>
</template>

<script>
import { getScholarshipList } from '../api/index'
// import LazyImage from '../utils/LazyImage'
export default {
  data() {
    return {
      loadingImg: require('assets/loading.gif'),
      imgList: []
    }
  },
  mounted() {
    this.initLoad()
    // this.$nextTick(() => {
    //   new LazyImage('.lazy-image')
    // })
  },
  methods: {
    initLoad() {
      try {
        // 异步错误-window.onerror
        setTimeout(() => {
          console.log(undefined.map())
        }, 1000)
      } catch (e) {
        console.log('捕获到setTimeout异常：', e)
      }

      getScholarshipList({ opendId: 'omsXu0ugFvGziGtY1Lyf0tAI9Noo' })
        .then(res => {})
        .catch(e => {})
      for (let index = 1; index <= 14; index++) {
        if (index >= 6) {
          this.imgList.push(require(`assets/demo${index}.jpg`))
        } else {
          this.imgList.push(require(`assets/demo${index}.png`))
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.img-box {
  border: 1px solid #d68585;
  img {
    display: flex;
    width: 600px;
    height: 600px;
  }
  .lazy-image {
    background: url('~assets/loading.gif') no-repeat center;
  }
}
</style>
