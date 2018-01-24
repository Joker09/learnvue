<template>
  <div class="slider" ref="slider">
      <ul class="slider__item--wrapper" ref="content">
        <li v-for="(img, i) in images" :key="i" class="slider__item">
          <a :href="img.link">
            <img :src="img.src" alt="">
          </a>
        </li>
      </ul>
  </div>
</template>

<script>
import BScroll from 'better-scroll';
export default {
  props: {
    images: {
      type: Array,
      default: null
    },
    loop: {
      type: Boolean,
      default: false
    }
  },
  mounted() {
    this.initSlider();
    window.addEventListener('resize', this.initSlider);
  },
  methods: {
    initSlider() {
      let l = this.images.length;
      this.itemWidth = this.$refs.slider.clientWidth;
      let items = this.$refs.slider.querySelectorAll('.slider__item');
      [].forEach.call(items, element => {
        element.style.width = `${this.itemWidth}px`;
      });

      this.$refs.content.style.width = `${l * this.itemWidth}px`;
      this.scroll = new BScroll(this.$refs.slider, {
        scrollX: true,
        scrollY: false,
        momentum: false,
        snap: {
          loop: this.loop,
          threshold: 0.3,
          speed: 400
        }
      });
    }
  }
};
</script>

<style>
.slider {
  width: 100%;
  overflow: hidden;
}

.slider__item--wrapper {
  margin: 0;
  padding: 0;
  list-style: none;
}

.slider__item {
  float: left;
}

.slider__item a {
  display: block;
}

.slider__item a img {
  width: 100%;
}
</style>
