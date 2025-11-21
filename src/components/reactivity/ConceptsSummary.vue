<template>
  <div class="bg-linear-to-r from-blue-500 to-purple-600 text-white rounded-lg shadow-md p-6">
    <h2 class="text-2xl font-semibold mb-4">Key Concepts</h2>
    <ul class="space-y-2">
      <li>
        ✅ <code class="bg-white/20 px-2 py-1 rounded">ref()</code> - for primitives, access with
        .value
      </li>
      <li>
        ✅ <code class="bg-white/20 px-2 py-1 rounded">reactive()</code> - for objects, direct
        property access
      </li>
      <li>
        ✅ <code class="bg-white/20 px-2 py-1 rounded">computed()</code> - cached derived state
      </li>
      <li>
        ✅ <code class="bg-white/20 px-2 py-1 rounded">watch()</code> - watch specific sources
        explicitly
      </li>
      <li>
        ✅ <code class="bg-white/20 px-2 py-1 rounded">watchEffect()</code> - automatic dependency
        tracking
      </li>
    </ul>
  </div>
</template>
