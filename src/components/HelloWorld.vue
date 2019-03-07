<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
      <p>A simple web viewer for KMyMoney</p>
    </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
  padding: 5px;
}
a {
  color: #42b983;
}
</style>
