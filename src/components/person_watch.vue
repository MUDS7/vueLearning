<template>
    <div class="person">
        <h2>姓名:{{ person.name }}</h2>
        <h2>年龄: {{ person.age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
    </div>
</template>

<script lang="ts" setup>
    import { ref, watch } from 'vue';

    // let name = ref('张三')
    // let age = ref(18)
    let person = ref({ name : '张三' , age : 18 }) 

    function changeName() {
        //name.value += '-'
        person.value.name += '-'
    }

    function changeAge() {
        //age.value += 1
        person.value.age += 1
    }

    // 修改ref基本类型可以直接这么写 ， 如果是 ref 结构体就需要用下面的写法
    //watch(age,(newValue,oldValue) => {
    //    console.log(newValue)
    //    if (newValue >= 20) {
    //        alert("hello")
    //    }
    //})

    // ref是结构体类型时的写法 , 如果不加下面的 {deep:true } 那么只有修改person的地址才会触发watch函数 例如: person.value = ref({ name : '李四' , age : 18 }) 
    // 如果使用 reactive  ， {deep:true}是开启的，且不能修改为false
    // watch第一个参数监视的是地址，所以不能直接传基本类型, 例如: watch( person.name )，
    // 其次在 person.value = ref({ name : '李四' , age : 18 }) 这样修改值得时候，也是无法触发watch函数，因为person对应的地址变了，watch监视的是原来的地址而不是变量,如果要也要监视地址变化的情况,加上 {deep : true } 也可以实现
    watch(person,(newValue,oldValue) => {
        console.log(newValue)
        if (newValue.age >= 20) {
            alert("hello")
        }
    },{deep: true})

    // 只监视结构体中某个字段的操作，因为watch只能不能监视基本类型,所以这个用了一个闭包函数进行监视，直接在外面定义一个function也是可以的,例如：watch(nameGetter，(newValue,oldValue) => { ... })
    function nameGetter() {
        return person.value.name
    }
    watch(() => { return person.value.name } , (newValue,oldValue) => {
        if (newValue == '张三-') {
            alert("hello")
        }
    }) 

    // 如果需要监视多个变量 ， 使用下方的写法,下方数组第一个元素因为是name是基本类型，所以需要闭包包一下，第二个是类型，本身watch就支持
    // watch([()=> { person.value.name} , person],(newValue,oldValue) => {
    //     
    // })
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