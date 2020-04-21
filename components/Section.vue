<template>
  <div class="menu__item">
    <a class="menu__item-link" :class="{hoverx: expand}" @click="$emit('expand')">{{section.title}}</a>
<!--    <img class="menu__item-img hidden" src="tiles/INSTAGRAM-05.jpg" alt="Some image"/>-->
    <div class="marquee">
      <div class="marquee__inner" aria-hidden="true">
        <span>{{section.title}}</span>
        <span>{{section.title}}</span>
        <span>{{section.title}}</span>
        <span>{{section.title}}</span>
      </div>
    </div>
    <transition
      @before-enter="beforeEnter"
      @enter="enter"
      @before-leave="beforeLeave"
      @leave="leave"
      name="accordion"
    >
    <div class="content menu__item-description" v-html="section.description"></div>
    </transition>
  </div>
</template>
<style>
  .menu__item-description {
    text-align: left;
    font-family: "Source Sans Pro", sans-serif;
    font-weight: 400;
    margin-top: 50px;
    max-width: 600px;
    margin: 50px auto;

    font-size: 1.5rem;
    line-height: 1.5;
  }

  .menu__item-description p {
    margin-bottom: 1em;
  }

  .accordion,
  .content {
    transition: 300ms ease-out;
  }
</style>
<script>
import inViewport from 'vue-in-viewport-mixin';

export default {
  props: {
    expand: {
      type: Boolean,
      default: false
    },
    section: {
      type: Object,
      default: 0
    },

  },
  mixins: [inViewport],
  watch: {
    'inViewport.now': function (visible) {
      console.log('This component is ' + (visible ? 'in-viewport' : 'hidden'));
    }
  },
  methods: {
    beforeEnter(el) {
      el.style.height = '0'
    },
    enter(el) {
      el.style.height = el.scrollHeight + 'px'
    },
    beforeLeave(el) {
      el.style.height = el.scrollHeight + 'px'
    },
    leave(el) {
      el.style.height = '0'
    }
  }
}
</script>
