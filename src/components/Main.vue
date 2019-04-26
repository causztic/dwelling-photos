<template>
  <div class="container">
    <img class="content-image" :src="img" />
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
      main: true,
      title: 'SIT Flats',
      img: '/static/1.png',
      content: 'Exploring historical reasons for the creation of the Singapore Improvement Trust, with its policies and architectural designs of its flats. <br /> <b>Click on any image below to start</b>'
    }
  },
  methods: {
    navigate: function (type) {
      if (type === 'dc') {
        this.img = '/static/dc/2.png'
        this.title = 'Dakota Crescent'
        this.content = 'Coming soon'
      }
    }
  }
}
</script>

<style scoped>
.container {
  min-height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.content {
  max-width: 500px;
  width: 100%;
}

.places {
  display: flex;
  flex-direction: column;
  align-items: center;
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
  height: 100vh;
  min-width: 800px;
  max-width: 100%;
}
</style>
