<template>
  <div class="select">
    <img :src="src" @mouseover="hover = true" @mouseleave="hover = false" @click="onClick" />
    <h2 :class="{active: hover}">{{text}}</h2>
  </div>
</template>

<script>
export default {
  name: 'ImageButton',
  props: {
    src: String,
    text: String,
    onClick: Function
  },
  data () {
    return {
      hover: false
    }
  }
}
</script>

<style scoped>
  img {
    width: 150px;
  }
  .select {
    width: 150px;
    overflow: auto;
    position: relative;
    padding: 6px;
  }
  h2 {
    display: none;
    top: 30%;
    left: 0;
    width: 100%;
    position: absolute;
    z-index: -1;
    font-size: 18px;
  }
  h2.active {
    display: block;
  }

  img:hover {
    opacity: 0.1;
    cursor: pointer;
  }
</style>
