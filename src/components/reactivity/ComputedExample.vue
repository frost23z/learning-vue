<script setup lang="ts">
import { ref, reactive, computed } from 'vue'

const count = ref(0)
const user = reactive({
  name: 'John Doe',
  age: 25,
})

const doubleCount = computed(() => count.value * 2)
const userInfo = computed(() => `${user.name} (${user.age} years old)`)

const increment = () => {
  count.value++
}

const updateAge = () => {
  user.age++
}
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-6">
    <h2 class="text-2xl font-semibold mb-4 text-green-600">3. computed() - Derived State</h2>
    <p class="text-gray-600 mb-4">
      <code class="bg-gray-100 px-2 py-1 rounded">computed()</code> creates cached values that
      update when dependencies change
    </p>

    <div class="space-y-4">
      <div class="space-y-3 bg-green-50 p-4 rounded">
        <div class="font-mono text-sm"><span class="text-gray-600">count =</span> {{ count }}</div>
        <div class="font-mono text-sm">
          <span class="text-gray-600">doubleCount =</span> {{ doubleCount }}
          <span class="text-gray-500"> (count × 2)</span>
        </div>
        <button
          @click="increment"
          class="px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600 transition text-sm"
        >
          Increment Count
        </button>
      </div>

      <div class="space-y-3 bg-green-50 p-4 rounded">
        <div class="font-mono text-sm">
          <span class="text-gray-600">user.name =</span> "{{ user.name }}"
        </div>
        <div class="font-mono text-sm">
          <span class="text-gray-600">user.age =</span> {{ user.age }}
        </div>
        <div class="font-mono text-sm">
          <span class="text-gray-600">userInfo =</span> "{{ userInfo }}"
        </div>
        <button
          @click="updateAge"
          class="px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600 transition text-sm"
        >
          Increment Age
        </button>
      </div>

      <p class="text-gray-600 text-sm mt-2">
        Computed values automatically recalculate when their dependencies change
      </p>
    </div>
  </div>
</template>
