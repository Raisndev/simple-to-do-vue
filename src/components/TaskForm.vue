<script lang="ts" setup>
import { ref } from 'vue';

const emit = defineEmits<{
    addTask: [newTask: string]
}>()

const newTask = ref('')

function formSubmitted() {
    emit('addTask', newTask.value)
}
</script>
<template>
    <form class="flex items-end gap-1.5" @submit.prevent="formSubmitted">
        <label class="flex flex-col">
            New Task
            <input class="border-1 border-solid rounded-md px-2 py-2" v-model="newTask" name="newTask" type="text" />
        </label>
        <button class="px-4 py-2 bg-slate-500 rounded-md text-white" type="submit">Add</button>
    </form>
</template>