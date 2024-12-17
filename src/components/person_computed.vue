<template>
    姓: <input type="text" v-model="firstName"> 
    <br>
    名: <input type="text" v-model="lastName">
    <br>
    全名: <span>{{  fullName }}</span>
    <br>
    全名: <span>{{  fullNameModify }}</span>
    <br>
    <button @click="changeName">修改name</button>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue';

    let firstName = ref('zhang')
    let lastName = ref('san')

    // 该写法fullName为只读 
    let fullName = computed(() => {
        return firstName.value.slice(0,1).toUpperCase() + firstName.value.slice(1) + '--' + lastName.value
    })

    let fullNameModify = computed({
        get() {
            return firstName.value.slice(0,1).toUpperCase() + firstName.value.slice(1) + '--' + lastName.value
        },
        set(v) {
            console.log("fullNameModify set")
            lastName.value = v
        }
    })

    // 此事件并为修改fullNameModify的值，而是将值传入了fullNameModigy computed函数的set方法
    function changeName() {
        fullNameModify.value = 'li'
    }
</script>