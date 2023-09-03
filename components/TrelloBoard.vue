<script setup lang="ts">
import { ref } from "vue";
import TrelloBoardTask from "./TrelloBoardTask.vue";
import DragHandle from "./DragHandle.vue";
import type { Column, Task } from "../types/index";
import draggable from "vuedraggable";
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
      {
        id: nanoid(),
        title: "Test ttitle task 2",
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
    <draggable
      v-model="columns"
      group="columns"
      item-key="id"
      :animation="150"
      handle=".drag-handle"
      class="flex gap-4 overflow-x-auto items-start"
    >
      <template #item="{ element: column }: { element: Column }">
        <div
          :key="column.id"
          class="column bg-gray-200 p-5 rounded min-w-[250px]"
        >
          <header class="font-bold mb-4">
            <DragHandle />
            {{ column.title }}
          </header>
          <draggable
            v-model="column.tasks"
            group="tasks"
            item-key="id"
            :animation="150"
            handle=".drag-handle"
          >
            <template #item="{ element: task }: { element: Task }">
              <TrelloBoardTask :task="task" />
            </template>
          </draggable>
          <footer>
            <button class="text-gray-500">+ Add to Cart</button>
          </footer>
        </div>
      </template>
    </draggable>
  </div>
</template>
