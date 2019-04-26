<template>
  <div class="select">
    <img :src="src" @mouseover="hover = true" @mouseleave="hover = false" />
    <h2 :class="{active: hover}">{{text}}</h2>
  </div>
</template>

<script>
export default {
  name: 'ImageButton',
  props: {
    src: String,
    text: String
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
    position: relative;
  }
  h2 {
    display: none;
  }
  h2.active {
    display: block;
  }

  img:hover {
    opacity: 0.5;
    cursor: pointer;
  }
</style>
