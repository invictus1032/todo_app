<template>
    <Header/>
    <Form v-bind:tasks="tasks"/>
</template>

<script setup>
import { ref } from "vue"
import Header from "./components/Header.vue"
import Form from "./components/Form.vue"

const tasks = ref([{name: "This is a sample todo", done: false}])
</script>

<style>
li {
    /* outline: solid 1px red;*/
} 

body {
    background-color: #fffaf0;
    display: grid;
    place-content: center;
}
</style>