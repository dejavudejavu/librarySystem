<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body,html {
    margin: 0;
    padding: 0;
    border: none;
}
.back-image{
    background: url("http://pic1.win4000.com/wallpaper/2020-11-27/5fc0c6c7406ac.jpg");
    /*background: #DCDFE6;*/
    background-size: 100%;
}
.search{
    background: #409EFF;
    min-height: 90px;
    margin: 10px;
    padding: 0px;
}
.search-item{
    width: 200px;
    float: left;
    margin: 10px;
}
.search-item:hover {
    margin-top: -2px;
}
.main{
    background: #909399;
    min-height: 500px;
    margin: 10px;
    padding: 0px;
}
</style>
