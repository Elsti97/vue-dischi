<template>
  <div>
    <div class="mt-5">
      <select v-model="valueOption">
        <option value="">All genres</option>
        <option :value="element" v-for="(element, index) in arrayGeneri" :key="index">{{element}}</option>
      </select>
    </div>
    
    <div>
      <DiskList :propsScelta="valueOption" @emitGeneri="methodsGeneri" />
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
  data(){
    return{
      valueOption: '',
      arrayGeneri: [],
    }
  },
  methods: {
      methodsGeneri(valoreEmit){
        this.arrayGeneri = valoreEmit
      }
    }
};
</script>

<style lang="scss" scoped>
  select{
    width: 10%;
  }
</style>