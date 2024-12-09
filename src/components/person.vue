<template>
    <div class="person">
        <h2>姓名:{{ name }}</h2>
        <h2>年龄:{{ age }}</h2>
        <button @click="showTel">点击显示电话号</button>
        <input v-model="name">
        <!--<button @click="changeName">修改名字</button> -->
        <button @click="addAge">增加年龄</button>
    </div>
</template>

<script lang="ts">
    export default {
        name:"person",
        data() {
            return {
                name:"张三",
                age: 18,
                tel: '123456789',
            }
        },
        methods: {
            showTel() {
                alert(this.tel)
            },
            changeName() {
                this.name = '李四'
            },
            addAge() {
                this.age +=1
            },
            
        },
    }
</script>

<style>
    .person{
        background-color: skyblue;
        box-shadow: 0 0 10px;
        border-radius: 10px;
        padding: 20px;
    }
    button {
        margin: 0 5px;
    }    
</style>