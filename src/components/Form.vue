<template>
    <section>
        <form @submit.prevent @submit="addTask">
            <label for="input_task">Add Todo</label>
            <input type="text" id="input_task" v-model="currentTask" required>
            <button>Add</button>
            <ul>
                <li v-for="(task, index) in tasks">
                    {{ task }}
                    <button @click="removeTask(index)">X</button>
                </li>
            </ul>
        </form>
    </section>
</template>

<script setup>
import { ref } from 'vue';
const { tasks } = defineProps({tasks: Array})

const currentTask = ref("")

function addTask() {
    if (currentTask.value === "") { return }
    tasks.push(currentTask.value);
    currentTask.value = "";
}

function removeTask(id) {
    tasks.splice(id, 1);
}
</script>

<style scoped>

</style>