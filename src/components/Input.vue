<template>
  <div class="input-model">
    <p>{{ message }}</p>
    <input class="input" v-model="message">
  </div>
</template>
<script>
  export default{
    name: 'Input',
    data: function(){
      return  { message:'hello Vue!' }
    }
  }
</script>
<style lang="scss" scoped>
  .input-model{
    .input{
      border: 1px solid #aaa;
      font-size:18px;
    }
  }
</style>