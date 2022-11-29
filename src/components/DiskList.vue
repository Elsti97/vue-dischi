<template>
  <div>
    <div class="d-flex flex-wrap rows mt-3 justify-content-center">
      <CardComp
        v-for="(element, index) in funzioneComputed"
        :key="index"
        :Album="element"
      />
    </div>
  </div>
</template>

<script>
import CardComp from "./CardComp.vue";
import axios from "axios";

export default {
  name: "DiskList",
  components: {
    CardComp,
  },
  props: {
    propsScelta: String,
  },
  data() {
    return {
      AlbumCop: [],
      arrayGeneri: [],
    };
  },
  computed: {
    funzioneComputed() {
      if (this.propsScelta == "") {
        return this.AlbumCop;
      } else {
        return this.AlbumCop.filter((element) => {
          return element.genre == this.propsScelta;
        });
      }
    },
  },
  mounted() {
    this.getAlbum();
  },
  methods: {
    getAlbum() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.AlbumCop = response.data.response;

          this.AlbumCop.forEach((singoloAlbum) => {
            if (!this.arrayGeneri.includes(singoloAlbum.genre)) {
              this.arrayGeneri.push(singoloAlbum.genre);
            }
          });

          this.$emit("emitGeneri", this.arrayGeneri);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
.rows {
  width: 60%;
  margin: auto;
}
</style>