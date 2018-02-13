<template>
  <div class="main">
    <Card style="width:320px">
         <div style="text-align:center;">
             <h3>lishuai test page</h3>
         </div>
     </Card>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main{
      text-align: center; /*让div内部文字居中*/
      background-color: #fff;
      border-radius: 20px;
      width: 320px;
      height: 350px;
      margin: auto;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
  }
</style>
