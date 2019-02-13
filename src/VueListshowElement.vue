<template>
  <div
    @mouseover="hover = true"
    @mouseleave="hover = false"
    class="wrapper-box"
    :class="{ 'should-grow': hover }"
  >
    <div class="content-box">
      <slot/>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    reduceOpacity: {
      require: true,
      type: Boolean
    },
    clear: {
      require: true,
      type: Boolean
    },

    opacity: {
      require: true,
      type: Number,
    },
  },

  data() {
    return {
      hover: false
    };
  },
  watch: {
    hover(e) {
      if (this.hover) {
        this.$emit("item-hovered");
        return;
      } else {
        this.$emit("item-unhovered");
      }
    },

    reduceOpacity() {
      if (this.reduceOpacity && !this.hover) {
        document
          .querySelectorAll(".wrapper-box")
          .forEach(e => (e.style.opacity = this.opacity));
      }
    },

    clear() {
      if (this.clear) {
        document
          .querySelectorAll(".wrapper-box")
          .forEach(e => (e.style.opacity = "1"));
      }
    }
  }
};
</script>

<style scoped>
.should-grow {
  flex-shrink: 1 !important;
  opacity: 1 !important;
}

.wrapper-box {
  padding: 10px;
}

.content-box {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
</style>
