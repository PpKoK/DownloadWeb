<template>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Microsoft YaHei', sans-serif; /* 设置微软雅黑字体 */
  font-weight: bold; /* 设置粗体 */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 19px;
  }
  
#building{
background-color:#ffffff ;
width:100%;
height:100%;
position:fixed;
background-size:100% 100%;}

body{
	margin:0;
	padding:0;
	border:0
}

</style>
