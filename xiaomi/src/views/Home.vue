<template>
  <div>
    <Header></Header>
  </div>
</template>

<script>
import axios from "axios";
import Header from '@/components/header';
export default {
  data() {
    return {
      nav:{},
      product:{}
    }
  },
  components: {
    Header,
  },
  created() {
    async function data(){
       return  await axios.get("/json/nav.json");
    }
    data().then(res=>{
      this.nav = res.data;
      console.log(this.nav);
    })
    async function data1(){
       return  await axios.get("/json/product.json");
    }
    data1().then(res=>{
      this.product = res.data;
      console.log(this.product);
    })
    
    
  },
};
</script>

<style lang="scss" scoped>
</style>
