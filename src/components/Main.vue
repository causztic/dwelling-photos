<template>
  <div class="container">
    <div class="image-container">
      <img class="content-image" :src="img" />
    </div>
    <img class="home-button" src="/static/icons/home.svg" />
    <div class="content">
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

export default {
  name: 'HelloWorld',
  components: { ImageButton },
  data () {
    return {
      title: 'SIT Flats',
      img: '/static/1.webp',
      content: 'Exploring historical reasons for the creation of the Singapore Improvement Trust, with its policies and architectural designs of its flats. <br /><ol><li>Some images on the left can be scrolled</li><li>Click on any image below to start</li>'
    }
  },
  methods: {
    navigate: function (type) {
      if (type === 'tb') {
        this.img = '/static/tb/1_ex.webp'
        this.title = 'Tiong Bahru'
        this.content = 'Coming soon'
      } else if (type === 'dc') {
        this.img = '/static/dc/1_ex.webp'
        this.title = 'Dakota Crescent'
        this.content = 'Coming soon'
      } else if (type === 'ks') {
        this.img = '/static/ks/1_ex.png'
        this.title = 'Kampung Silat'
        this.content = 'Coming soon'
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

.container {
  min-height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.content {
  display: flex;
  flex-direction: column;
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

.image-container {
  height: 100vh;
  overflow: auto;

}

.content-image {
  width: 100%;
  min-height: 100vh;
  margin-bottom: -6px;
}
</style>
