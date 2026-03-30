<template>
  <div
    class="group flex w-full max-w-md mx-auto flex-col overflow-hidden rounded-xl bg-gray-900 border border-none transition-all hover:scale-[1.015] drop-shadow-[4px_4px_0_#7836cf]"
  >
    <img
      :src="imagen"
      :alt="`Proyecto: ${titulo}`"
      class="h-52 p-3 w-full object-cover rounded-2xl"
    />

    <div class="flex flex-col grow p-3">
      <h3 class="text-lg font-semibold mb-2 text-white drop-shadow-[1px_1px_0_#7836cf]">
        {{ titulo }}
      </h3>

      <div class="flex flex-wrap gap-2 mb-4">
        <span
          v-for="tech in tecnologias"
          :key="tech"
          class="rounded-md bg-[#7836cf]/20 text-[#a27ed1] px-2 py-0.5 text-xs font-semibold"
        >
          {{ tech }}
        </span>
      </div>

      <div class="mt-auto flex justify-between gap-3">
       <a
  :href="demo || '#'"
  target="_blank"
  rel="noopener noreferrer"
  :class="[
    'w-full text-center border py-1.5 rounded-md text-sm font-semibold transition-colors',
    demo
      ? 'border-[#7836cf] text-[#7836cf] hover:bg-[#7836cf] hover:text-gray-900'
      : 'border-gray-600 text-gray-600 cursor-not-allowed pointer-events-none'
  ]"
>
  Demo
</a>

<a
  :href="codigo || '#'"
  target="_blank"
  rel="noopener noreferrer"
  :class="[
    'w-full text-center border py-1.5 rounded-md text-sm font-semibold transition-colors',
    codigo
      ? 'border-[#7836cf] text-[#7836cf] hover:bg-[#7836cf] hover:text-gray-900'
      : 'border-gray-600 text-gray-600 cursor-not-allowed pointer-events-none'
  ]"
>
  Código
</a>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  titulo: String,
  imagen: String,
  tecnologias: Array,
  demo: String,
  codigo: String
})
</script>