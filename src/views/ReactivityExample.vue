<script setup lang="ts">
import RefExample from '@/components/reactivity/RefExample.vue'
import ReactiveExample from '@/components/reactivity/ReactiveExample.vue'
import ComputedExample from '@/components/reactivity/ComputedExample.vue'
import WatchExample from '@/components/reactivity/WatchExample.vue'
import TodoExample from '@/components/reactivity/TodoExample.vue'
import ConceptsSummary from '@/components/reactivity/ConceptsSummary.vue'
</script>

<template>
  <div class="min-h-screen bg-gray-50 py-12 px-4">
    <div class="max-w-4xl mx-auto space-y-8">
      <div class="text-center">
        <h1 class="text-4xl font-bold text-gray-900 mb-2">Vue 3 Reactivity System</h1>
        <p class="text-gray-600">Interactive examples of Vue's reactive primitives</p>
      </div>

      <RefExample />
      <ReactiveExample />
      <ComputedExample />
      <WatchExample />
      <TodoExample />
      <ConceptsSummary />
    </div>
  </div>
</template>
