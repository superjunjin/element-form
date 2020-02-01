<template>
  <div>
      <!-- @input监听input输入 :value绑定value值-->
      <input type="text" :value="valuek" @input="onInput">
  </div>
</template>

<script>
export default {
    props:['valuek'],
    methods: {
        onInput(e){
            let value = e.target.value;
            //子组件发送给父组件改变input值
            this.$emit('inputk', value);
        }
    }
}
</script>

<style>

</style>