<template>
    <div class="task">
        <h3>{{ task.title }}</h3>
        <div class="icons">
            <i @click="taskStore.deleteTask(task.id)" class="material-icons">delete</i>
            <i 
                class="material-icons"
                :class="{active: task.isFav}"
                @click="taskStore.toggleFav(task.id)" 
                >
                favorite</i>
        </div>
    </div>
</template>

<script setup>
import { defineProps, ref } from 'vue';
import { useTaskStore } from '../stores/taskStore';

const props = defineProps(["task"]);
const taskStore = useTaskStore();

</script>

<style scoped>

</style>