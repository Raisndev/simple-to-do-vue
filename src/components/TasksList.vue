<script lang="ts" setup>
import { Task } from '@/types';

const props = defineProps<{
    tasks: Task[]
}>()
</script>

<template>
    <div class="flex flex-col gap-2 mt-3">
        <article class="bg-slate-200 rounded-md py-2 px-4" v-for="task in props.tasks" :key="task.id">
            <label class="flex gap-2">
                <input  type="checkbox"/>
                {{ task.name }}
            </label>
        </article>
    </div>
</template>