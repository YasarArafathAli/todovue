<template>
  <div class="hello">
    <h1>{{msg}}</h1>
  </div>
</template>

<script>
export default {
  name: 'MainHeading',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
  background: var( #f5f5f5);
  color: #333333;
}
h1 {
  font-family: 'Permanent Marker',cursive;
  letter-spacing: 5px;
  margin: 0 0 20px;
  font-size: 60px;
  color: #349f4b;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
