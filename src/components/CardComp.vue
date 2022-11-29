<template>
  <div>
    <div class="card mx-2 mt-3 py-2">
      <img :src="Album.poster" alt="copertina album" />
      <h2>{{ Album.title }}</h2>
      <p>{{ Album.author }}</p>
      <p>{{ Album.year }}</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: "CardComp",
    props: {
    Album: Object,
  },

  }
</script>

<style lang="scss" scoped>
.card{
  height: 270px;
  width: 150px;
  background-color: #2e3946;
  img {
    width: 120px;
    aspect-ratio: 1/1;
    align-self: center;
  }
  h2 {
    color: white;
    font-size: 1.2rem;
    margin: 1rem 0;
  }
  p {
    color: #7e776e;
    line-height: .5rem;
  }
}
</style>