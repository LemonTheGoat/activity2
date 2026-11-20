<script setup lang="ts">
type ButtonColor = 'primary' | 'secondary' | 'emerald' | 'rose' | 'slate'

interface Props {
  label: string
  color?: ButtonColor
  to?: string
  type?: 'button' | 'submit' | 'reset'
  disabled?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  color: 'primary',
  to: undefined,
  type: 'button',
  disabled: false,
})

const emit = defineEmits<{ click: [event: MouseEvent] }>()

const colorClasses: Record<ButtonColor, string> = {
  primary:
    'bg-sky-600 text-white shadow-md shadow-sky-600/30 hover:bg-sky-500 focus-visible:ring-sky-500',
  secondary:
    'bg-slate-800 text-white shadow-md shadow-slate-800/30 hover:bg-slate-700 focus-visible:ring-slate-500',
  emerald:
    'bg-emerald-600 text-white shadow-md shadow-emerald-600/30 hover:bg-emerald-500 focus-visible:ring-emerald-500',
  rose: 'bg-rose-600 text-white shadow-md shadow-rose-600/30 hover:bg-rose-500 focus-visible:ring-rose-500',
  slate:
    'bg-white text-slate-700 ring-1 ring-inset ring-slate-300 hover:bg-slate-100 hover:text-slate-900 focus-visible:ring-sky-500',
}

const classes = computed(() => [
  'inline-flex items-center justify-center gap-2 rounded-xl px-4 py-2.5 text-sm font-semibold transition duration-200 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:ring-offset-slate-50 disabled:cursor-not-allowed disabled:opacity-50',
  colorClasses[props.color],
])
</script>

<template>
  <!-- Renders a router link when `to` is provided, otherwise a plain button -->
  <NuxtLink
    v-if="to"
    :to="to"
    :class="classes"
    @click="emit('click', $event)"
  >
    {{ label }}
  </NuxtLink>
  <button
    v-else
    :type="type"
    :disabled="disabled"
    :class="classes"
    @click="emit('click', $event)"
  >
    {{ label }}
  </button>
</template>
