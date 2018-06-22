<template>
  <div id="app">
  	<!-- header -->
    <app-header :poiInfo="poiInfo"></app-header>

    <!-- nav -->
    <app-nav></app-nav>
	  <!-- content -->
    <router-view></router-view>
  </div>
</template>

<script>

import Header from './components/header/Header.vue'
import Nav from './components/nav/Nav.vue'

export default {
  	name: 'App',
    data(){
      return{
        poiInfo:{}
      }
    },
  	components:{
  		"app-header":Header,
      "app-nav":Nav
  	},
    created(){
      // axios

      // fetch
      fetch("api/goods").then(res=>{
        return res.json()
      }).then(response=>{
        // console.log(response)
        if (response.code == 0) {
          this.poiInfo = response.data.poi_info;
          // console.log(this.poiInfo)
        }
      })
    }
}
</script>

<style>

</style>  
