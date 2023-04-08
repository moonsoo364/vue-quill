<template>
  <div id="app">
    <div class="route-set">
      <router-link to = "/" >handler</router-link>
      <router-link to = "/format">format</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
.route-set{
  text-align: center;
  margin : 0 0 16px 0;
}
.route-set >a{
  margin : 0 0 8px;
}
</style>
