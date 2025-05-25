<script lang="ts" setup>
import { Task } from '@/types';

const props = defineProps<{
    tasks: Task[]
}>()

const emits = defineEmits<{
    toggleDone: [id: string]
}>()
</script>

<template>
    <div class="flex flex-col gap-2 mt-3">
        <article class="bg-slate-200 rounded-md py-2 px-4" :class="{ 'done-task': task.done }" v-for="task in props.tasks" :key="task.id">
            <label class="flex gap-2">
                <input @input="emits('toggleDone', task.id)" :checked="task.done" type="checkbox"/>
                <span :class="{ done: task.done }">{{ task.name }}</span>
            </label>
        </article>
    </div>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
.done-task {
    opacity:  .5;
}
article {
    transition: all .3s ease;
}
</style>