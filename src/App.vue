<template>

  <div>
    <PoemManager/>
  </div>

</template>

<script>
import PoemManager from './components/PoemManager.vue';


export default{
  name:'App',
  components:{
    PoemManager
  }
};

</script>


<style>
#app {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
  background: rgba(255, 255, 255, 0.1);
}
</style>

