<template>
    <section>
        <form @submit.prevent @submit="addTask">
            <label for="input_task">Add Todo</label>
            <input type="text" id="input_task" v-model="currentTask" required>
            <button>Add</button>
            <ul>
                <li v-for="(task, index) in tasks" :class="{done: task.done}">
                    {{ task.name }}
                    <button @click.prevent @click="markTaskAsDone(index)">✔</button>
                    <button @click.prevent @click="removeTask(index)">X</button>
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
    tasks.push({name: currentTask.value, done:false});
    currentTask.value = "";
}

function markTaskAsDone(index) {
    tasks[index].done = !tasks[index].done
}

function removeTask(index) {
    tasks.splice(index, 1);
}
</script>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>