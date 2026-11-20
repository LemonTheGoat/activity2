<script setup lang="ts">
interface Props {
  title: string
  description: string
}

defineProps<Props>()
</script>

<template>
  <article
    class="group flex h-full flex-col rounded-2xl border border-slate-200 bg-white p-6 shadow-sm transition duration-300 hover:-translate-y-1 hover:border-sky-300 hover:shadow-lg"
  >
    <div
      class="mb-4 flex h-11 w-11 items-center justify-center rounded-xl bg-sky-50 text-sky-600 transition duration-300 group-hover:bg-sky-600 group-hover:text-white"
      aria-hidden="true"
    >
      <svg
        class="h-5 w-5"
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.8"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M14 3H7a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8l-5-5Z"
        />
        <path stroke-linecap="round" stroke-linejoin="round" d="M14 3v5h5" />
        <path stroke-linecap="round" stroke-linejoin="round" d="M9 13h6" />
        <path stroke-linecap="round" stroke-linejoin="round" d="M9 17h4" />
      </svg>
    </div>

    <h3 class="text-base font-semibold text-slate-900">
      {{ title }}
    </h3>

    <p class="mt-2 text-sm leading-relaxed text-slate-600">
      {{ description }}
    </p>
  </article>
</template>
