<script setup lang="ts">
interface Props {
  name: string
  studentId: string
  program: string
  yearLevel: string
  status: string
  avatarColor?: string
}

const props = withDefaults(defineProps<Props>(), {
  avatarColor: '#0284c7',
})

const initials = computed(() =>
  props.name
    .split(' ')
    .filter(part => part.length > 0)
    .slice(0, 2)
    .map(part => part.charAt(0))
    .join('')
    .toUpperCase(),
)

const statusStyles: Record<string, string> = {
  Regular: 'bg-emerald-50 text-emerald-700 ring-emerald-600/20',
  Irregular: 'bg-amber-50 text-amber-700 ring-amber-600/20',
  Transferee: 'bg-sky-50 text-sky-700 ring-sky-600/20',
  Graduating: 'bg-violet-50 text-violet-700 ring-violet-600/20',
  'On Leave': 'bg-rose-50 text-rose-700 ring-rose-600/20',
}

const statusClass = computed(
  () => statusStyles[props.status] ?? 'bg-slate-100 text-slate-600 ring-slate-500/20',
)
</script>

<template>
  <article
    class="group flex h-full flex-col rounded-2xl border border-slate-200 bg-white p-5 shadow-sm transition duration-300 hover:-translate-y-1 hover:border-sky-300 hover:shadow-xl"
  >
    <div class="flex items-center gap-4">
      <div
        class="flex h-12 w-12 shrink-0 items-center justify-center rounded-full text-sm font-bold text-white ring-4 ring-slate-100 transition duration-300 group-hover:ring-sky-100"
        :style="{ backgroundColor: avatarColor }"
        aria-hidden="true"
      >
        {{ initials }}
      </div>

      <div class="min-w-0">
        <h3 class="truncate text-base font-semibold text-slate-900">{{ name }}</h3>
        <p class="mt-0.5 truncate text-xs font-medium tracking-wide text-slate-500">
          {{ studentId }}
        </p>
      </div>
    </div>

    <p class="mt-4 text-sm leading-relaxed text-slate-600">{{ program }}</p>

    <div class="mt-auto flex items-center justify-between gap-2 border-t border-slate-100 pt-4">
      <span
        class="inline-flex items-center rounded-lg bg-slate-100 px-2.5 py-1 text-xs font-semibold text-slate-600"
      >
        {{ yearLevel }}
      </span>

      <span
        class="inline-flex items-center gap-1.5 rounded-full px-2.5 py-1 text-xs font-semibold ring-1"
        :class="statusClass"
      >
        <span class="h-1.5 w-1.5 rounded-full bg-current opacity-70" aria-hidden="true" />
        {{ status }}
      </span>
    </div>
  </article>
</template>
