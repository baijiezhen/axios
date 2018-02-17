<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  created() {
     console.log(1);
      // this.$axios.get('http://dyapi.cwfpp.cn/index/index/index').then((res)=>{
      //    console.log(res);
      // })
    //  this.$ajax.get('index/index/index').then((res)=>{
    //     console.log(res);
    //  })
    this.$ajax.post('/api/postcomment/13',{content:'nihoa'}, {
    headers: {
                                'Content-Type': 'application/x-www-form-urlencoded'
   } }).then((res)=>{
         console.log(res.data)
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
