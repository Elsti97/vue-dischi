<template>
  <div>
    <select v-model="valueOption">
      <option :value="elem" v-for="(elem, index) in arrayGeneri" :key="index">{{elem}}</option>
    </select>
    <div>
      <DiskList />
    </div>
  </div>

</template>

<script>
import DiskList from './DiskList.vue'

export default {
  name: "MainComp",
  components: {
    DiskList,
  },
  props: {
      arrayGeneri: String,
    },
  data(){
      return{
        valueOption: '',
      }
  },
};
</script>

<style lang="scss" scoped>

</style>