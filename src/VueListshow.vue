<template>
  <div>
    <div class="boxes">
      <vue-listshow-element v-for="(item, index) in items" :key="index"
        @item-hovered="action"
        @item-unhovered="clearEffects"
        :clear="clear"
        :reduceOpacity="reduceOpacity"
        :opacity="opacity"
        :class="classes"
        :style="{ 'transition': `${transition}ms`}"
      >
        <slot :item="item"/>
      </vue-listshow-element>
    </div>

  </div>
</template>

<script>

import VueListshowElement from "./VueListshowElement";

export default {
  props: {
    items: {
      default: true,
    },
    transition: {
      default: 300,
      type: Number,
    },
    opacity: {
      default: .7,
      type: Number,
    },
    classes: {
      type: String
    },
  },

  data () {
    return {
      reduceOpacity: false,
      clear: false
    }
  },

  components: {
    VueListshowElement
  },

  methods: {
    action (e) {
      this.reduceOpacity = true
      this.clear = false
    },

    clearEffects () {
      this.reduceOpacity = false
      this.clear = true
    }
  },

  mounted () {}
}
</script>

<style scoped>

  .boxes {
    display: flex;
    flex-direction: row;
  }

  .boxes > div {
    flex-shrink: 2;
    overflow: hidden;
  }

  @media screen and (max-width: 576px) {
    .boxes {
      display: flex;
      flex-direction: column;
    }
  }
</style>
