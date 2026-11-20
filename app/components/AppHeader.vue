<script setup lang="ts">
const route = useRoute()

const links = [
  { label: 'Home', to: '/' },
  { label: 'Students', to: '/students' },
]

const isActive = (to: string) => route.path === to
</script>

<template>
  <header class="sticky top-0 z-40 border-b border-slate-200 bg-white/90 backdrop-blur">
    <div class="mx-auto flex h-16 max-w-6xl items-center justify-between gap-4 px-4 sm:px-6">
      <!-- Brand -->
      <NuxtLink to="/" class="group flex items-center gap-3">
        <span
          class="flex h-9 w-9 items-center justify-center rounded-lg bg-sky-600 text-sm font-bold text-white shadow-md shadow-sky-600/30 transition duration-200 group-hover:bg-sky-500"
        >
          SI
        </span>
        <span class="flex flex-col">
          <span class="text-sm font-bold leading-tight tracking-tight text-slate-900 sm:text-base">
            Student Information
          </span>
          <span class="text-[11px] font-medium leading-tight text-slate-500">BSIT Portal</span>
        </span>
      </NuxtLink>

      <!-- Navigation -->
      <nav class="flex items-center gap-1 sm:gap-2" aria-label="Main navigation">
        <NuxtLink
          v-for="link in links"
          :key="link.to"
          :to="link.to"
          class="rounded-lg px-3 py-2 text-sm font-semibold transition duration-200 sm:px-4"
          :class="
            isActive(link.to)
              ? 'bg-sky-600 text-white shadow-md shadow-sky-600/30'
              : 'text-slate-600 hover:bg-slate-100 hover:text-slate-900'
          "
          :aria-current="isActive(link.to) ? 'page' : undefined"
        >
          {{ link.label }}
        </NuxtLink>
      </nav>
    </div>
  </header>
</template>
