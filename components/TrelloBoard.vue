<script setup lang="ts">
import { ref } from "vue";
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
  <div>
    <div v-for="column in columns" :key="column.id">
      <header>
        {{ column.title }}
      </header>
      <p v-for="task in column.tasks" :key="task.id">
        {{ task.title }}
      </p>
    </div>
  </div>
</template>
