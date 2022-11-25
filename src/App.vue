<template>
  <div id="app">
    <HeaderComp />
    <div class="d-flex flex-wrap rows mt-5 justify-content-center">
      <MainComp v-for="(element, index) in AlbumCop" :key="index" :Album="element" />
    </div>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp,
  },
  data(){
    return{
      AlbumCop: '',
    }
  },
  mounted(){
    this.getAlbum();
  },
  methods: {
    getAlbum(){
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((response) =>{
        this.AlbumCop = response.data.response;
      });
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  background-color: #1E2D3B;
  height: 100vh;
  
  .rows{
    width: 60%;
    margin: auto;
  }
}
</style>
