<script setup lang="ts">
import { reactive } from 'vue'

const user = reactive({
  name: 'John Doe',
  age: 25,
  email: 'john@example.com',
})

const updateUser = () => {
  user.age++
  user.name = `User ${user.age}`
}

const resetUser = () => {
  user.name = 'John Doe'
  user.age = 25
  user.email = 'john@example.com'
}
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-6">
    <h2 class="text-2xl font-semibold mb-4 text-purple-600">2. reactive() - Reactive Objects</h2>
    <p class="text-gray-600 mb-4">
      Use <code class="bg-gray-100 px-2 py-1 rounded">reactive()</code> for objects and arrays
    </p>
    <div class="space-y-4">
      <div class="grid gap-3">
        <div class="bg-purple-50 p-3 rounded">
          <span class="font-semibold">Name:</span> {{ user.name }}
        </div>
        <div class="bg-purple-50 p-3 rounded">
          <span class="font-semibold">Age:</span> {{ user.age }}
        </div>
        <div class="bg-purple-50 p-3 rounded">
          <span class="font-semibold">Email:</span> {{ user.email }}
        </div>
      </div>
      <div class="flex gap-2">
        <button
          @click="updateUser"
          class="px-4 py-2 bg-purple-500 text-white rounded hover:bg-purple-600 transition"
        >
          Update User
        </button>
        <button
          @click="resetUser"
          class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600 transition"
        >
          Reset
        </button>
      </div>
    </div>
  </div>
</template>
