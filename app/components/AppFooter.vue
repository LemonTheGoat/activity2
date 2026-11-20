<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<template>
  <footer class="border-t border-slate-200 bg-white">
    <div
      class="mx-auto flex max-w-6xl flex-col items-center gap-4 px-4 py-8 text-center sm:flex-row sm:items-start sm:justify-between sm:px-6 sm:text-left"
    >
      <!-- Copyright -->
      <div>
        <p class="flex items-center justify-center gap-2 text-sm font-bold text-slate-900 sm:justify-start">
          <span
            class="flex h-7 w-7 items-center justify-center rounded-md bg-sky-600 text-[10px] font-bold text-white"
            aria-hidden="true"
          >
            SI
          </span>
          Student Information Website
        </p>
        <p class="mt-2 text-xs text-slate-500">
          © {{ year }} · All rights reserved. Built with Nuxt 4 &amp; Tailwind CSS.
        </p>
      </div>

      <!-- Course info -->
      <div class="text-center sm:text-right">
        <p class="text-sm font-semibold text-slate-700">
          BS Information Technology – Caraga State University
        </p>
        <p class="mt-1 text-xs text-slate-500">
          Course: BS Information Technology (BSIT) · Reusable Components &amp; Props
        </p>
      </div>
    </div>
  </footer>
</template>
