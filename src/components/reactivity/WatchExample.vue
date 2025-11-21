<script setup lang="ts">
import { ref, reactive, watch, watchEffect } from 'vue'

const count = ref(0)
const user = reactive({
  age: 25,
})

// watch() - watch specific reactive sources
watch(count, (newVal, oldVal) => {
  console.log(`watch: Count changed from ${oldVal} to ${newVal}`)
})

// Watch multiple sources
watch([count, () => user.age], ([newCount, newAge], [oldCount, oldAge]) => {
  console.log(`watch: Count: ${oldCount} → ${newCount}, Age: ${oldAge} → ${newAge}`)
})

// watchEffect() - automatic dependency tracking
watchEffect(() => {
  console.log(`watchEffect: count is ${count.value}, age is ${user.age}`)
})

const increment = () => {
  count.value++
}

const incrementAge = () => {
  user.age++
}

const reset = () => {
  count.value = 0
  user.age = 25
}
</script>

<template>
  <div class="bg-white rounded-lg shadow-md p-6">
    <h2 class="text-2xl font-semibold mb-4 text-orange-600">4. watch() & watchEffect()</h2>
    <p class="text-gray-600 mb-4">
      Watch reactive sources and perform side effects. Check the browser console for logs!
    </p>

    <div class="space-y-4">
      <div class="bg-orange-50 p-4 rounded space-y-3">
        <p class="text-sm">
          <span class="font-semibold">watch():</span> Explicitly watch specific sources
        </p>
        <p class="text-sm">
          <span class="font-semibold">watchEffect():</span> Automatically tracks dependencies
        </p>
      </div>

      <div class="flex items-center gap-4">
        <div class="text-lg">
          Count: <span class="font-bold">{{ count }}</span>
        </div>
        <div class="text-lg">
          Age: <span class="font-bold">{{ user.age }}</span>
        </div>
      </div>

      <div class="flex gap-2">
        <button
          @click="increment"
          class="px-4 py-2 bg-orange-500 text-white rounded hover:bg-orange-600 transition"
        >
          Increment Count
        </button>
        <button
          @click="incrementAge"
          class="px-4 py-2 bg-orange-500 text-white rounded hover:bg-orange-600 transition"
        >
          Increment Age
        </button>
        <button
          @click="reset"
          class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600 transition"
        >
          Reset
        </button>
      </div>

      <p class="text-sm text-gray-600 bg-yellow-50 p-3 rounded">
        💡 Open DevTools Console (F12) and click the buttons to see watchers in action!
      </p>
    </div>
  </div>
</template>
