<template>
    <div class="header">
        <input type="text" placeholder="输入日程安排,回车键确认" v-model="title" @keyup.enter="addItems"/>
    </div>
</template>

<script>
    export default {
        name: "header",
        data(){
            return{
                title:''
            }
        },
        props:{
            addTodo:Function
        },
        methods:{
            addItems(){
                //1.判断title不为空
                const title=this.title.trim()//去空格
                if(!title){
                    alert("输入的任务不能为空")
                    return ;
                }
                //2.生成一个todo对象
                let todo={title,finished:false}
                //3.调用父组件的插入方法
                this.addTodo(todo)
                //4.清空输入框
                this.title=''
            }
        }

    }
</script>

<style scoped>
    .header input{
        font-size: 15px;
        width: 560px;
        border: #ccc 1px solid;
        border-radius:4px;
        padding:4px 7px;
        outline: none;
    }
    .header input:focus{
        outline: none;
        border-color: rgba(255,0,0,0.8);
        box-shadow: inset 0 1px 1px rgba(255,0,0,0.075),0 0 4px rgba(255,0,0,0.6);
    }
</style>