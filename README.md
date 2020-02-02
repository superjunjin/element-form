# element-form（实现FormItem和Form）

## 自定义组件input实现v-model双向数据绑定
- v-model实际做了两件事：绑定value值和监听input事件
- 自定义组件input需要自己定义v-model的逻辑
- :valuek="value" @inputk="value = arguments[0]"  相当于  v-model实现的内容
- 现在需要换成v-model的话，input组件中的valuek和inputk必须换成value和input，以便和v-model默认定义的值一致，才能发挥作用

## 父子传值，跨多层传值，用注入
- 父：provide(){
        return {
            someval:'来自app.vue'
        }
    } 
- 子：inject: ['someval']
- Form的rules就注入到了FormItem中

## slot
- FormItem组件的slot传入Input组件
- Form组件的slot传入FormItem组件

## 校验器async-validator
- 自定义组件Input向父组件FormItem发送校验方法
this.$parent.$emit('validate')
- FormItem监听到校验方法，进行校验

## ref
- 获取原生dom
- 调用原生方法setAttribute控制自动补全框的隐藏
