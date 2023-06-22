<template>
    <Header/>
    <Form v-bind:tasks="tasks"/>
</template>

<script setup>
import { ref } from "vue"
import Header from "./components/Header.vue"
import Form from "./components/Form.vue"

const tasks = ref([])
</script>

<style>
body {
    background-color: skyblue;
}
</style>