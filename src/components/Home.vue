<template>
    <div>
        <h3>留言板</h3>
        <input type="text" v-model="msg">
        <button @click="add_note">发表留言</button>
        <br>
        <ul>
            <li v-for="(message,index) in msg_list" :key="index">
                {{message}}<a href="javascript:;" @click="delNote(index)">删除</a>
            </li>
        </ul>
        <span>总数量：{{msg_list.length}}条</span>
        <input type="button" value="删除所有" @click="delAll" v-show="msg_list.length!=0">
    </div>
</template>

<script>
    export default {
        name: "Home",
        data:function () {
            return {
                msg:'',
                msg_list: localStorage.msg ? JSON.parse(localStorage.msgs) : [],
            }
        },
        methods:{
            add_note(){
                //完成留言的添加
                let msg = this.msg;
                if(msg){
                    this.msg_list.push(this.msg);
                    // 将用户发表的数据持久化到localStorage
                    // 储存前将数据进行序列化
                    localStorage.msgs = JSON.stringify(this.msg_list);
                    this.msg = "";
                }
            },
            delNote(index) {
                console.log(index);
                // 根据下标去删除数组中的某个元素
                this.msg_list.splice(index, 1); // 参数1：从哪个下标开始删除 参数2：删除几个元素
                localStorage.removeItem('msgs');
                localStorage.msgs = JSON.stringify(this.msg_list);

            },
            delAll() {
                this.msg_list = [];
                localStorage.clear();
            },
        }
    }
</script>

<style scoped>

</style>
