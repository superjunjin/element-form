<template>
    <div>
        <!-- v-model实际做了两件事：绑定value值和监听input事件 -->
        {{value}}
        <k-input :valuek="value" @inputk="value = arguments[0]"></k-input>

        <h3>element表单</h3>
        <hr />
        <!-- ref注册表单的引用信息 -->
        <el-form :model="model" :rules="rules" ref="loginForm">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="model.username" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="确认密码" prop="password">
                <el-input type="password" v-model="model.password" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm('loginForm')">提交</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
import KInput from "./components/Input.vue";
export default {
    name: "app",
    components: {
        KInput
    },
    data() {
        return {
            value:'1111',
            // 绑定数据
            model: { username: "tom", password: "" },
            // 检验规则
            rules: {
                username: [
                    { required: true, message: "清输入用户名" },
                    { min: 6, max: 10, message: "请输入6-10位的用户名"}
                ],
                password: [{ required: true, message: "请输入密码" }]
            }
        };
    },
    methods: {
        submitForm(form) {
            // $refs引用表单的引入信息，进行检验
            this.$refs[form].validate(valid=>{
                if(valid){
                    alert('请求登录');
                }else{
                    alert('校验失败');
                }
            })
        }
    }
};
</script>

<style>

</style>
