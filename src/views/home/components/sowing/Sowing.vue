<template>
  <swiper id="swiper"
          :options="swiperOption"
          ref="mySwiper">
    <!--slides-->
    <swiper-slide v-for="(sowing,index) in sowing_list"
                  :key="sowing.public_id">
        <img :src="sowing.icon_url"
             :alt="sowing.public_name">
    </swiper-slide>

    <div class="swiper-pagination" slot="pagination">

    </div>
  </swiper>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import {  swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name: "Sowing",
  props: {
    sowing_list:Array
  },
  data() {
    return {
      swiperOption: {
        //进来就加载
        notNextTick:true,
        pagination: {
          el: '.swiper-pagination',
        },
        loop: true,
        //配置自动播放
        autoplay: {
          delay: 3000,
          //最后一个是否停止
          stopOnLastSlide:false,
          // 用户操作swiper 之后，是否禁止autoplay
          disableOnInteraction: false,
        },
        observer: true,
        observeParents: true,
        //配置速度
        speed: 600,
        //滑动后回调函数
        on: {
          sliderChangeTransitionEnd () {

          },
          //preventLinksPropagation: false
        }
      }
    }
  },
  components: {
    swiper,
    swiperSlide
  },
  mounted () {

  },
  computed: {

    //拿到swiper对象
    swiper () {
      return this.$refs.mySwiper.swiper;
    }
  }
}
</script>

<style scoped>
  #swiper {
    width: 100%;
    height: 14rem;
  }
  #swiper img {
    width:100%;
    height:100%
  }
  #swiper >>> .swiper-pagination-bullet-active {
    background-color: #75a342;
  }
  #swiper >>> .swiper-pagination-bullet {
    width: 0.3rem;
    height: 0.3rem;
    border-radius: 0;
  }
</style>