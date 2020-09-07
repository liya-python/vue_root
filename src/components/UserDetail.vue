<template>
    <div>
        用户详情页：需要接收到当前要查看的用户的详细信息 <br>
        id==={{$route.params.id}} <br>
        name==={{$route.params.name}} <br>
        生日==={{$route.params.bir}} <br>
        个人信息==={{$route.params.content}} <br>
        <h4>用户详情展示</h4>
        <br>
        <button @click="goBack">返回首页</button>
        <button @click="goPage">返回用户列表页</button>
    </div>
</template>

<script>
    export default {
        name: "UserDetail",
        methods:{
            goPage(){
                this.$router.push({path: "/user"});
            },
            goBack(){
                // this.$router.go(-1);
                this.$router.push("/");

            },

        }
    }
</script>

<style scoped>

</style>
