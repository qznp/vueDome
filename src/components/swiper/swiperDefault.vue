<template>
  <div>
    <swiper :options="swiperOption">
      <swiper-slide class="swiper-slide" v-for="(item, index) in slide" :key="index">Slide {{item}}</swiper-slide>
      <!-- 分页器 -->
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>
<script>
import "swiper/dist/css/swiper.css";
import { swiper, swiperSlide } from "vue-awesome-swiper";
export default {
  data() {
    return {
      slide: [1, 2, 3, 4, 5, 6],
      swiperOption: {
        //   竖屏切换
        direction: "vertical",
        // 无限回滚
        loop: true,
        // 分页器
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        }
      }
    };
  },
  components: {
    swiper,
    swiperSlide
  }
};
</script>
<style scoped>
.swiper-slide {
  height: 4rem;
  text-align: center;
  padding-top: 3rem;
  border-bottom: 1px solid #ccc;
}
</style>
