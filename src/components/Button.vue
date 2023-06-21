<template>
    <section>
        <form @submit.prevent @submit="addTask">
            <label for="input_task">Add Todo</label>
            <input type="text" id="input_task" v-model="currentTask" required>
            <button>Add</button>
            <ul>
                <li v-for="task in tasks">
                    {{ task }}
                </li>
            </ul>
        </form>
    </section>
</template>

<script setup>
import { ref } from 'vue';

const currentTask = ref("")
const tasks = ref([])

function addTask() {
    if (currentTask.value === "") { return }
    tasks.value.push(currentTask.value);
    currentTask.value = "";
}
</script>

<style scoped>

</style>