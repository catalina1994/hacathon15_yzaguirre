<template>
 <div>
    <!-- <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div> -->
   <banner subtitle="Hacktahon 15" title="PELICULAS"></banner>
  <router-view/>
 </div>
</template>
<script>
import banner from '@/components/banner';
export default {
  name:'app',
  components:{
    banner
  }
}
</script>

<style lang="scss">

</style>
