<template>
  <div>
    <swiper class="swiper" :options="swiperOption">
      <swiper-slide class="text">
        <div class="centent">
          重点看一下options的加入属性：
          direction：'vertical'设置竖排显示
          slidesPerView:'auto' 设置同屏显示的数量，默认为1，这里使用auto是随意的意思。
          freeMode:true 默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper，设置为true则变为free模式，slide会根据惯性滑动可能不止一格且不会贴合。
          mousewheel:true 开启鼠标滚轮控制Swiper切换。可设置鼠标选项，或true使用默认值。
          只要掌握好这些属性，其实做出文本滑动效果是非常简单的。
          重点看一下options的加入属性：
          direction：'vertical'设置竖排显示
          slidesPerView:'auto' 设置同屏显示的数量，默认为1，这里使用auto是随意的意思。
          freeMode:true 默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper，设置为true则变为free模式，slide会根据惯性滑动可能不止一格且不会贴合。
          mousewheel:true 开启鼠标滚轮控制Swiper切换。可设置鼠标选项，或true使用默认值。
          只要掌握好这些属性，其实做出文本滑动效果是非常简单的。
          重点看一下options的加入属性：
          direction：'vertical'设置竖排显示
          slidesPerView:'auto' 设置同屏显示的数量，默认为1，这里使用auto是随意的意思。
          freeMode:true 默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper，设置为true则变为free模式，slide会根据惯性滑动可能不止一格且不会贴合。
          mousewheel:true 开启鼠标滚轮控制Swiper切换。可设置鼠标选项，或true使用默认值。
          只要掌握好这些属性，其实做出文本滑动效果是非常简单的。
          重点看一下options的加入属性：
          direction：'vertical'设置竖排显示
          slidesPerView:'auto' 设置同屏显示的数量，默认为1，这里使用auto是随意的意思。
          freeMode:true 默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper，设置为true则变为free模式，slide会根据惯性滑动可能不止一格且不会贴合。
          mousewheel:true 开启鼠标滚轮控制Swiper切换。可设置鼠标选项，或true使用默认值。
          只要掌握好这些属性，其实做出文本滑动效果是非常简单的。
          重点看一下options的加入属性：
          direction：'vertical'设置竖排显示
          slidesPerView:'auto' 设置同屏显示的数量，默认为1，这里使用auto是随意的意思。
          freeMode:true 默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper，设置为true则变为free模式，slide会根据惯性滑动可能不止一格且不会贴合。
          mousewheel:true 开启鼠标滚轮控制Swiper切换。可设置鼠标选项，或true使用默认值。
          只要掌握好这些属性，其实做出文本滑动效果是非常简单的。
        </div>
      </swiper-slide>
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
        // 设置同屏显示的数量，默认为1，auto为随意
        slidesPerView: "auto",
        // 默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper
        // 设置为true则变为free模式，slide会根据惯性滑动可能不止一格不会贴合
        freeMode: true,
        // 开启鼠标滚轮控制是swiper切换。可设置鼠标选项，或true使用默认值
        mousewheel: true
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
.swiper {
  height: 300px;
  overflow: hidden;
}
.text {
  font-size: 18px !important;
  text-align: left;
  padding: 30px;
  height: auto;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
</style>
