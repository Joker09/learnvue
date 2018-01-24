<template>
  <div id="app">
    <v-rating :size='30'></v-rating>
    <div class="slider-wrapper">
      <v-slider :images="images" v-if="images"></v-slider>
      <v-loading v-show="!images" type="spin"></v-loading>
    </div>
  </div>
</template>

<script>
import vRating from 'components/v-rating';
import vSlider from 'components/v-slider';
import vLoading from 'vue-loading-template';
export default {
  name: 'app',
  data() {
    return {
      images: null
    };
  },
  created() {
    setTimeout(() => {
      this.images = [
        {
          src:
            'http://www.prestigetraining.org/wp-content/uploads/2015/11/Fotolia_35877734_Subscription_Monthly_XXL-700x400.jpg',
          link: 'http://www.baidu.com'
        },
        {
          src:
            'https://cache.carlsonhotels.com/galleries/radblu/hotels/cities/Cesme-700x400.jpg',
          link: 'http://www.qq.com'
        }
      ];
    }, 2000);
  },
  components: {
    vRating,
    vSlider,
    vLoading
  }
};
</script>

<style>

</style>
