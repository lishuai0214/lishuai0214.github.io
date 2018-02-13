<template>
  <div class="main">
     <h3>lishuai test page</h3>
     <Button @click="instance('info')">Info</Button>
     <Button @click="instance('success')">Success</Button>
     <Button @click="instance('warning')">Warning</Button>
     <Button @click="instance('error')">Error</Button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
 methods: {
     instance (type) {
         const title = 'Title';
         const content = '<p>Content of dialog</p><p>Content of dialog</p>';
         switch (type) {
             case 'info':
                 this.$Modal.info({
                     title: title,
                     content: content
                 });
                 break;
             case 'success':
                 this.$Modal.success({
                     title: title,
                     content: content
                 });
                 break;
             case 'warning':
                 this.$Modal.warning({
                     title: title,
                     content: content
                 });
                 break;
             case 'error':
                 this.$Modal.error({
                     title: title,
                     content: content
                 });
                 break;
         }
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
