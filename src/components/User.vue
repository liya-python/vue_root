<template>
    <div>这是我的用户组件
        <h3>用户列表页</h3>
        <input type="text" v-model="name">
        <input type="text" v-model="bir">
        <input type="text" v-model="content">
        <button @click="add_user">添加用户</button>
        <table border="2">
            <tr>
                <td>ID</td>
                <td>姓名</td>
                <td>生日</td>
                <td>个人信息</td>
                <td>操作</td>

            </tr>
            <tr v-for="user in users" :key="user.id">
                <td>{{user.id}}</td>
                <td>{{user.username}}</td>
                <td>{{user.bir}}</td>
                <td>{{user.content}}</td>
                <td><a href="javascript:;" @click="del_user(`${user.id}`)">删除</a>| <router-link :to="`/detail/${user.id}/${user.bir}/${user.username}/${user.content}`">查看详情</router-link></td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: "User",
        data:function () {
            return {
                id:2,
                name:'',
                bir:'',
                content:'',
                users: [
                    {id:1,username:'小黑',bir:'2012-12-12',content:'介绍'},
                    {id:2,username:'小白',bir:'2012-12-12',content:'介绍'},
                ],
            }

        },
        methods:{
            del_user(id){
                console.log(id);
                this.users.splice((id-1), 1)
            },
            add_user(){
                this.id ++;
                this.users.push({id:this.id,username:this.name,bir:this.bir,content:this.content});
                this.name='';
                this.bir='';
                this.content = '';
            }
        }
    }
</script>

<style scoped>

</style>
