<template>
  <div class="container">
    <img src="../assets/1.png" />
    <div class="content">
      <h1>SIT Flats</h1>
      <p>
        Exploring historical reasons for the creation of the Singapore Improvement Trust, with its policies
        and architectural designs of its flats.
      </p>
      <div class="places">
        <ImageButton :src="require('../assets/tb/1.jpeg')" text="Tiong Bahru" />
        <ImageButton :src="require('../assets/d/1.png')" text="Dakota" />
        <ImageButton :src="require('../assets/ks/1.jpeg')" text="Kampung Silat" />
      </div>
    </div>
  </div>
</template>

<script>
import ImageButton from './ImageButton.vue'

export default {
  name: 'HelloWorld',
  components: { ImageButton }
}
</script>

<style scoped>
.container {
  height: 100vh;
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
}

h1 {
  width: 100%;
  text-align: center;
}
p {
  margin: 40px;
}
img {
  height: 100%;
  max-width: 100%;
}
</style>
