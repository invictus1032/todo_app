<template>
    <section>
        <form @submit.prevent @submit="addTask">
            <label for="input_task">Add Todo</label>
            <input type="text" id="input_task" v-model="currentTask" required placeholder="Add new todo">
            <button class="add_button">Add</button>
            <ul>
                <li v-for="(task, index) in tasks" :class="{done: task.done}">
                    <span>{{ task.name }}</span>
                    <span class="task_modifier">
                        <button class="mark_done_button" @click.prevent @click="markTaskAsDone(index)">✔</button>
                        <button class="remove_task_button" @click.prevent @click="removeTask(index)">X</button>
                    </span>
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
    form {
        width: 60vw;
    }
    label {
        font-size: 1.2em;
        font-weight: bold;
    }
    input {
        font-size: 1em;
        margin: 10px 0;
        padding: 10px 10px;
        width: 100%;
    }
    .add_button {
        color: white;
        font-size: 16px;
        padding: 0.5em 3em;
        background-color: rgb(21, 189, 21);
    }
    ul {
        font-size: 1.3rem;
        padding: 0;
    }
    li {
        display: flex;
        background-color: rgb(236, 167, 167);
        justify-content: space-between;
        list-style: none;
        width: 100%;
        margin: 10px 0;
        padding: 20px 0;
        padding-left: 30px;

    }
    .task_modifier {
        padding-right: 30px;
    }
    .task_modifier button {
        margin-left: 10px;
        font-size: 1em;
    }
    .mark_done_button {
        background-color: aqua;
    }
    .remove_task_button {
        background-color: red;
    }
</style>