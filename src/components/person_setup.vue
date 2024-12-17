<template>
    <div class="person">
        <h2>姓名:{{ name }}</h2>
        <h2>年龄:{{ age }}</h2>
        <h2>语文成绩:{{ chinese }}</h2>
        <h2>数学成绩:{{ match }}</h2>
        <button @click="showTel">点击显示电话号</button>
        <input v-model="name">
        <!--<button @click="changeName">修改名字</button> -->
        <button @click="addAge">增加年龄</button>
        <button @click="addScore">修改成绩</button>
        <h2>游戏列表</h2>
        <ul>
            <li v-for="g in games" :key="g.id">
                {{  g.name }}
            </li>
        </ul>
    </div>
</template>

<!--标准setup方法写法-->
<!--
<script lang="ts">
    export default {
        name:"person_setup",
        setup() {
            let name = '张三'
            let age = 18
            let tel = '123456789'

            function showTel() {
                alert(tel)
            }

            function addAge() {
                age += 1
            }

            return { name , age , showTel,addAge }
        } 
    }
</script>
-->

<!--setup 语法糖写法-->
<script lang="ts" setup>
    import { ref, toRef, toRefs } from 'vue';
    import { reactive } from 'vue';

    let name = '张三'
    let age = ref(18)
    let tel = '123456789'

    let score = reactive({chinese: 98 , match: 100 })
    let games = reactive([
        { id:'1', name: '123' },
        { id:'2', name: '456' },
        { id:'3', name: '789' }      
    ])

    // 如果直接使用 let { chinese , match } = score ， chinese 和 match 就不是响应式对象 就不能修改值
    // toRefs是将score中的每一个字段都加上ref()，所以需要使用.value才能修改值
    let {chinese,match} = toRefs(score)
    // toRef 就是将score中某个字段加上 ref()
    //let chinese = toRef(score,'chinese')

    function showTel() {
        alert(tel)
    }

    function addAge() {
        age.value +=1
    }

    function addScore() {
        chinese.value += 10
        match.value +=10
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