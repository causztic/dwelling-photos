<template>
  <div class="container">
    <progressive-img class="content-image" :src="img" />
    <img class="home-button" :class="{ disabled: main }" src="/static/icons/home.svg" @click="() => navigate('home')" />
    <div class="content">
      <div class="controls" :class="{ disabled: main }">
        <img src="/static/icons/left-arrow.svg" @click="previousImage"/>
        <img src="/static/icons/right-arrow.svg" @click="nextImage"/>
      </div>
      <h1>{{title}}</h1>
      <p v-html="content"></p>
      <div class="places">
        <ImageButton src="/static/tb/1.jpeg" text="Tiong Bahru" :onClick="() => navigate('tb')" />
        <ImageButton src="/static/dc/1.png" text="Dakota Crescent" :onClick="() => navigate('dc')" />
        <ImageButton src="/static/ks/1.jpeg" text="Kampung Silat" :onClick="() => navigate('ks')" />
      </div>
    </div>
  </div>
</template>

<script>
import ImageButton from './ImageButton.vue'

const originalTitle = 'SIT Flats'
const originalContent = 'Exploring historical reasons for the creation of the Singapore Improvement Trust, with its policies and architectural designs of its flats. <br /><ol><li>Some images on the left can be scrolled</li><li>Click on any image below to start</li>'
const imageLengths = { 'tb': 18, 'dc': 5, 'ks': 11 }

export default {
  name: 'HelloWorld',
  components: { ImageButton },
  data () {
    return {
      main: true,
      title: originalTitle,
      img: '/static/1.webp',
      content: originalContent,
      area: 'main',
      imageIndices: { 'tb': 1, 'dc': 1, 'ks': 1 }
    }
  },
  methods: {
    previousImage: function () {
      if (this.imageIndices[this.area] === 1) {
        this.imageIndices[this.area] = imageLengths[this.area]
      } else {
        this.imageIndices[this.area] -= 1
      }
      this.img = `/static/${this.area}/${this.imageIndices[this.area]}_ex.webp`
    },
    nextImage: function () {
      if (this.imageIndices[this.area] === imageLengths[this.area]) {
        this.imageIndices[this.area] = 1
      } else {
        this.imageIndices[this.area] += 1
      }
      this.img = `/static/${this.area}/${this.imageIndices[this.area]}_ex.webp`
    },
    navigate: function (type) {
      this.area = type
      if (type === 'tb') {
        this.main = false
        this.img = '/static/tb/1_ex.webp'
        this.title = 'Tiong Bahru'
        this.content = 'Coming soon'
      } else if (type === 'dc') {
        this.main = false
        this.img = '/static/dc/1_ex.webp'
        this.title = 'Dakota Crescent'
        this.content = 'Coming soon'
      } else if (type === 'ks') {
        this.main = false
        this.img = '/static/ks/1_ex.webp'
        this.title = 'Kampung Silat'
        this.content = 'Coming soon'
      } else {
        this.main = true
        this.img = '/static/1.webp'
        this.title = originalTitle
        this.content = originalContent
      }
    }
  }
}
</script>

<style scoped>
.home-button {
  position: absolute;
  right: 12px;
  top: 22px;
  width: 32px;
  cursor: pointer;
}

.home-button:hover {
  opacity: 0.5;
}

.disabled {
  opacity: 0;
  cursor: initial;
}

.controls {
  position: absolute;
  top: 22px;
  left: -90px;
  z-index: 2;
  padding: 6px 0 0 3px;
  background-color: rgba(255,255,255,0.5);
}

.controls img {
  width: 32px;
  margin-right: 16px;
  cursor: pointer;
}

.container {
  min-height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.content {
  display: flex;
  flex-direction: column;
  width: 490px;
  position: relative;
}

.places {
  display: flex;
  margin-top: auto;
  flex-direction: row;
  justify-content: space-around;
  align-items: flex-end;
  width: 100%;
}

h1 {
  width: 100%;
  text-align: center;
}

p {
  margin: 40px;
}

.content-image {
  overflow: auto;
  height: 100vh;
}

</style>
