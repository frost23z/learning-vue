<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)

const increment = () => {
  count.value++
}

const decrement = () => {
  count.value--
}
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-6">
    <h2 class="text-2xl font-semibold mb-4 text-blue-600">1. ref() - Reactive Primitives</h2>
    <p class="text-gray-600 mb-4">
      Use <code class="bg-gray-100 px-2 py-1 rounded">ref()</code> for primitive values (numbers,
      strings, booleans)
    </p>
    <div class="space-y-4">
      <div class="flex items-center gap-4">
        <button
          @click="decrement"
          class="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600 transition"
        >
          -
        </button>
        <div class="text-3xl font-bold min-w-[100px] text-center">{{ count }}</div>
        <button
          @click="increment"
          class="px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600 transition"
        >
          +
        </button>
      </div>
      <div class="bg-blue-50 p-4 rounded">
        <p class="font-mono text-sm">count.value = {{ count }}</p>
        <p class="text-gray-600 text-sm mt-2">
          Access with <code class="bg-white px-1 rounded">.value</code> in script, directly in
          template
        </p>
      </div>
    </div>
  </div>
</template>
