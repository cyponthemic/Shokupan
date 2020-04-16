<template>
  <div class="menu__item">
    <a class="menu__item-link" :class="{'hover' : !inViewport.now && animate }">{{section.title}}</a>
    <img class="menu__item-img" src="~assets/logo.svg" alt="Some image"/>
    <div class="menu__item-description" v-html="section.description"></div>
    <div class="marquee">
      <div class="marquee__inner" aria-hidden="true">
        <span>{{section.title}}</span>
        <span>{{section.title}}</span>
        <span>{{section.title}}</span>
        <span>{{section.title}}</span>
      </div>
    </div>
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
  }
</style>
<script>
import inViewport from 'vue-in-viewport-mixin';

export default {
  props: {
    animate: {
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
  }
}
</script>
