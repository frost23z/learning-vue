<script setup lang="ts">
import { ref, reactive, computed } from 'vue'

interface Todo {
  id: number
  text: string
  done: boolean
}

const todos = reactive<Todo[]>([
  { id: 1, text: 'Learn ref()', done: true },
  { id: 2, text: 'Learn reactive()', done: true },
  { id: 3, text: 'Learn computed()', done: false },
  { id: 4, text: 'Learn watchers', done: false },
])

const newTodo = ref('')
const completedTodos = computed(() => todos.filter((todo) => todo.done))
const pendingTodos = computed(() => todos.filter((todo) => !todo.done))

const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.push({
      id: Date.now(),
      text: newTodo.value,
      done: false,
    })
    newTodo.value = ''
  }
}

const toggleTodo = (todo: Todo) => {
  todo.done = !todo.done
}

const removeTodo = (id: number) => {
  const index = todos.findIndex((todo) => todo.id === id)
  if (index > -1) {
    todos.splice(index, 1)
  }
}
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-6">
    <h2 class="text-2xl font-semibold mb-4 text-indigo-600">5. Practical Example: Todo List</h2>
    <p class="text-gray-600 mb-4">
      Combining ref(), reactive(), and computed() in a real application
    </p>

    <!-- Add Todo Form -->
    <div class="flex gap-2 mb-4">
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        type="text"
        placeholder="Add a new todo..."
        class="flex-1 px-4 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-indigo-500"
      />
      <button
        @click="addTodo"
        class="px-6 py-2 bg-indigo-500 text-white rounded hover:bg-indigo-600 transition"
      >
        Add
      </button>
    </div>

    <!-- Stats -->
    <div class="flex gap-4 mb-4 text-sm">
      <div class="bg-blue-100 px-3 py-1 rounded">Total: {{ todos.length }}</div>
      <div class="bg-green-100 px-3 py-1 rounded">Completed: {{ completedTodos.length }}</div>
      <div class="bg-yellow-100 px-3 py-1 rounded">Pending: {{ pendingTodos.length }}</div>
    </div>

    <!-- Todo List -->
    <div class="space-y-2">
      <div
        v-for="todo in todos"
        :key="todo.id"
        class="flex items-center gap-3 p-3 bg-gray-50 rounded hover:bg-gray-100 transition"
      >
        <input
          type="checkbox"
          :checked="todo.done"
          @change="toggleTodo(todo)"
          class="w-5 h-5 text-indigo-600 rounded focus:ring-2 focus:ring-indigo-500"
        />
        <span :class="{ 'line-through text-gray-400': todo.done }" class="flex-1">
          {{ todo.text }}
        </span>
        <button
          @click="removeTodo(todo.id)"
          class="px-3 py-1 bg-red-500 text-white text-sm rounded hover:bg-red-600 transition"
        >
          Delete
        </button>
      </div>
    </div>
  </div>
</template>
