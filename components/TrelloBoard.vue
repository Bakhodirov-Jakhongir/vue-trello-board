<script setup lang="ts">
import { ref } from "vue";
import TrelloBoardTask from "./TrelloBoardTask.vue";
import type { Column, Task } from "../types/index";
import { nanoid } from "nanoid";
const columns = ref<Column[]>([ 
  {
    id: nanoid(),
    title: "Backlog",
    tasks: [
      {
        id: nanoid(),
        title: "Test ttitle task",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "Selected for Dev",
    tasks: [
      {
        id: nanoid(),
        title: "task",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "In progress ",
    tasks: [
      {
        id: nanoid(),
        title: "Test ttitle task",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "QA",
    tasks: [
      {
        id: nanoid(),
        title: "Test ttitle task",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "Completed",
    tasks: [
      {
        id: nanoid(),
        title: "Test ttitle task",
        createdAt: new Date(),
      },
    ],
  },
]);
</script>
<template>
  <div class="flex gap-4 overflow-x-auto items-start">
    <div
      v-for="column in columns"
      :key="column.id"
      class="column bg-gray-200 p-5 rounded min-w-[250px]"
    >
      <header class="font-bold mb-4">
        {{ column.title }}
      </header>
      <TrelloBoardTask v-for="task in column.tasks" :task="task" />
      <footer>
        <button class="text-gray-500">+ Add to Cart</button>
      </footer>
    </div>
  </div>
</template>
