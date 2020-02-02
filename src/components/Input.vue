<template>
  <div>
      <!-- {{someval}} -->
      <!-- @input监听input输入 :value绑定value值-->
      <input ref="inputk" :type="type" :value="value" @input="onInput" v-on:blur="onblur('inputk')" v-on:focus="onfocus('inputk')"  autocomplete="off">
  </div>
</template>

<script>
export default {
    inject: ['someval'],
    props:{
        value:{
            type: String,
            default: ''
        },
        type:{
            type: String,
            default: 'text'
        }
    },
    methods: {
        onInput(e){
            let value = e.target.value;
            //子组件发送给父组件改变input值
            this.$emit('input', value);
            this.$parent.$emit('validate')
        },
        onblur(input){
            this.$refs[input].setAttribute('readonly',true);
        },
        onfocus(input){
            this.$refs[input].removeAttribute('readonly');
        }
    }
}
</script>

<style>

</style>