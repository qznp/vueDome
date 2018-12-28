<template>
  <div>
    <!--search bar layout-->
    <div class="search-bar">
      <van-row>
        <van-col span="3">
          <img :src="locationIcon" width="80%" class="location-icon">
        </van-col>
        <van-col span="16" class="search-input"></van-col>
        <van-col span="5">
          <van-button size="mini">查找</van-button>
        </van-col>
      </van-row>
    </div>
    <!-- swiper-area -->
    <div class="swiper-area">
      <van-swipe :autoplay="1000">
        <van-swipe-item v-for="(banner,index) in bannerPicArray" :key="index">
          <img v-lazy="banner.image" width="100%">
        </van-swipe-item>
      </van-swipe>
    </div>
    <!-- type-bar -->
    <div class="type-bar">
      <div v-for="(cate,index) in category" :key="index">
        <img v-lazy="cate.image" width="90%">
        <span>{{cate.mallCategoryName}}</span>
      </div>
    </div>
    <!-- ad banner area -->
    <div class="ad-banner">
      <img v-lazy="adBanner.PICTURE_ADDRESS" width="100%">
    </div>
    <!-- 商品推荐 -->
    <div class="recommend-area">
      <div class="recommend-title">商品推荐</div>
      <div class="recommend-body">
        <!-- swiper -->
        <swiper :options="swiperOption">
          <swiper-slide v-for="(item,index) in recommendGoods " :key="index">
            <div class="recommend-item">
              <img :src="item.image" width="80%">
              <div>{{item.goodsName}}</div>
              <div>￥{{item.price | moneyFilter}}(￥{{item.mallPrice | moneyFilter}})</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
    <!-- <swiperDefault></swiperDefault> -->
    <!-- floor -->
    <floorComponent :floorData="floor1" :floorTitle="floorName.floor1"></floorComponent>
    <floorComponent :floorData="floor2" :floorTitle="floorName.floor2"></floorComponent>
    <floorComponent :floorData="floor3" :floorTitle="floorName.floor3"></floorComponent>
    <!-- hot area -->
    <div class="hot-area">
      <div class="hot-title">热卖商品</div>
      <div class="hot-goods">
        <!-- list -->
        <div class="hot-goods">
          <van-list>
            <van-row gutter="20">
              <van-col span="12" v-for="( item, index) in hotGoods" :key="index">
                <goods-info
                  :goodsImage="item.image"
                  :goodsName="item.name"
                  :goodsPrice="item.price"
                ></goods-info>
              </van-col>
            </van-row>
          </van-list>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import "swiper/dist/css/swiper.css";
import { swiper, swiperSlide } from "vue-awesome-swiper";
// import swiperDefault from "../swiper/swiperDefault";
import floorComponent from "../component/floorComponent.vue";
import { toMoney } from "@/filter/moneyFilter.js";
import url from "@/serviceAPI.config.js";
import goodsInfo from "../component/goodsInfoComponent";
export default {
  components: {
    swiper,
    swiperSlide,
    // swiperDefault
    floorComponent,
    goodsInfo
  },
  data() {
    return {
      msg: "shopping",
      locationIcon: require("../../assets/images/location.png"),
      bannerPicArray: [],
      category: [],
      adBanner: [],
      recommendGoods: [],
      swiperOption: {
        slidesPerView: 3
      },
      floor1: [],
      floor2: [],
      floor3: [],
      floorName: {},
      hotGoods: [] //热卖商品
    };
  },
  filters: {
    moneyFilter(money) {
      return toMoney(money);
    }
  },
  created() {
    axios({
      url: url.getShoppingMallInfo,
      method: "get"
    })
      .then(response => {
        if (response.status == 200) {
          console.log(response.data.data.hotGoods);
          // 轮播图片
          this.bannerPicArray = response.data.data.slides;
          // 分类
          this.category = response.data.data.category;
          // 广告
          this.adBanner = response.data.data.advertesPicture;
          // 推荐商品
          this.recommendGoods = response.data.data.recommend;
          // 楼层1
          this.floor1 = response.data.data.floor1;
          // 楼层2
          this.floor2 = response.data.data.floor2;
          // 楼层3
          this.floor3 = response.data.data.floor3;
          // 楼层名
          this.floorName = response.data.data.floorName;
          // 热卖商品
          this.hotGoods = response.data.data.hotGoods;
        }
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>
<style scoped>
.search-bar {
  height: 2.2rem;
  background-color: #e5017d;
  line-height: 2.2rem;
}
.search-input {
  /* width: 100%; */
  height: 1.3rem;
  border-top: 0px;
  border-left: 0px;
  border-right: 0px;
  border-bottom: 1px solid #ffffff !important;

  background-color: #e5017d;
  color: #fff;
}
.location-icon {
  padding-top: 0.2rem;
  padding-left: 0.3rem;
}
/* 轮播图 */
.swiper-area {
  clear: both;
  max-height: 9.3rem;
  overflow: hidden;
}
/* type-bar */
.type-bar {
  background-color: #fff;
  margin: 0 0.3rem 0.3rem 0.3rem;
  border-radius: 0.3rem;
  font-size: 14px;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
}
.type-bar div {
  padding: 0.3rem;
  font-size: 12px;
  text-align: center;
  flex: 1;
}
/* 商品推荐 */
.recommend-area {
  background-color: #fff;
  margin-top: 0.3rem;
}
.recommend-title {
  border-bottom: 1px solid #eee;
  font-size: 14px;
  padding: 0.2rem;
  color: #e5017d;
}
.recommend-body {
  border-bottom: 1px solid #eee;
}
.recommend-item {
  width: 99%;
  border-right: 1px solid #eee;
  font-size: 12px;
  text-align: center;
}
/* hot */
.hot-area {
  text-align: center;
  font-size: 14px;
  height: 1.8rem;
  line-height: 1.8rem;
}
</style>


