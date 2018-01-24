<template>
  <div class="rating">
    <ul class="rating__content">
      <li @click="changeStar(i)" v-for="i in maxStars" :key="i" class="rating__star" :class="i <= stars ? 'rating__star--active' : ''">
        <icon :name="i <= stars ? 'star' : 'star-o'"></icon>
      </li>
    </ul>
    <span class="rating__counter">{{counter}}</span>
  </div>
</template>


<script>
import 'vue-awesome/icons/star';
import 'vue-awesome/icons/star-o';

import Icon from 'vue-awesome/components/Icon';
export default {
  name: 'v-stars',
  data() {
    return {
      stars: this.defaultStar
    };
  },
  props: {
    defaultStar: {
      type: Number,
      default: 3
    },
    size: {
      type: Number,
      default: 20
    },
    maxStars: {
      type: Number,
      default: 5
    }
  },
  computed: {
    counter() {
      return `${this.stars} of ${this.maxStars}`;
    }
  },
  created() {},
  methods: {
    changeStar(i) {
      setTimeout(() => {
        this.stars = i;
      }, 0);
    }
  },
  components: {
    Icon
  }
};
</script>


<style>
.rating {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 14px;
  color: #a7a8a8;
}

.rating__content {
  display: flex;
  margin: 0;
  padding: 0;
  list-style: none;
}

.rating__content:hover .rating__star {
  color: #f3d23e;
}

.rating__star {
  margin: 5px;
  cursor: pointer;
}

.rating__star:hover ~ .rating__star {
  color: inherit;
}
.rating__star--active {
  color: #f3d23e;
}
</style>
