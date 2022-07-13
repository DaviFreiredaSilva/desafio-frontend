<template>
  <MainHeader/>
  <ShopForm :formHandler="formHandler" />
</template>

<script>
import ShopForm from './components/ShopForm.vue';
import MainHeader from './components/MainHeader.vue';

export default {
  name: 'App',
  components: {
    MainHeader,
    ShopForm
  },
  methods: {
    formHandler: function(){
      alert("Teste")
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
