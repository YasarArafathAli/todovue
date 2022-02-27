<template>
<div class="container">
  <MainHeading msg="Todo App"/>
  <AddInput/>
</div>
</template>

<script>
import MainHeading from './components/MainHeading.vue'
import AddInput from './components/AddInput.vue'
export default {
  name: 'App',
  components: {
    MainHeading,
    AddInput
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap');

#app {
  font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol";
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 18px;
}
.container{
  max-width: 800px;
  margin: auto;
}


</style>
