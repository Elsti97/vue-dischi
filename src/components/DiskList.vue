<template>
  <div>
    <div class="d-flex flex-wrap rows mt-5 justify-content-center">
      <CardComp  v-for="(element, index) in AlbumCop" :key="index" :Album="element"  />
    </div>
  </div>
</template>

<script>
import CardComp from './CardComp.vue';
import axios from 'axios'

  export default {
    name: "DiskList",
    components: {
      CardComp,
    },
  data(){
    return{
      AlbumCop: [],
      arrayGeneri: [],
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

        this.AlbumCop.forEach((singoloAlbum)=>{
          if(!this.arrayGeneri.includes(singoloAlbum.genre)){
            this.arrayGeneri.push(singoloAlbum.genre)
          }
        })
      });
    },
  }
}
</script>

<style lang="scss" scoped>
.rows{
    width: 60%;
    margin: auto;
  }
</style>