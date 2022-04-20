<template>
  <div id="app">
    <HeaderView />
    <router-view/>
    <FooterView />
  </div>
</template>

<script>
import HeaderView from './components/HeaderView'
import FooterView from './components/FooterView'

export default {
  name:"App",
  components:{
    HeaderView,
    FooterView
  }
}


</script>


<style >
@import url("./assets/css/main.css");
/*@import url("./assets/css/card-list.css");*/
</style>
