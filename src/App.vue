<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import 'normalize.css'
export default {
  name: 'App'
}
</script>

<style lang="less">
  * {
    margin:0;
    padding:0;
  }
  body {
    background-color: #f0f3ef
  }
</style>
