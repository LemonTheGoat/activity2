<script setup lang="ts">
useHead({ title: 'Home | Student Information Website' })

const featuredStudents = [
  {
    name: 'Maria Santos',
    studentId: '2024-IT-0117',
    program: 'BS Information Technology',
    yearLevel: '1st Year',
    status: 'Regular',
    avatarColor: '#0284c7',
  },
  {
    name: 'Angela Reyes',
    studentId: '2023-IT-0442',
    program: 'BS Information Technology',
    yearLevel: '2nd Year',
    status: 'Irregular',
    avatarColor: '#0f766e',
  },
  {
    name: 'Liza Abundo',
    studentId: '2021-IT-0044',
    program: 'BS Information Technology',
    yearLevel: '4th Year',
    status: 'Graduating',
    avatarColor: '#f59e0b',
  },
]

const lastAction = ref('')

const scrollToOverview = () => {
  document.getElementById('overview')?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}

const showAction = (action: string) => {
  lastAction.value = action
}
</script>

<template>
  <div>
    <!-- Hero -->
    <section class="relative overflow-hidden bg-slate-900 text-white">
      <div
        class="pointer-events-none absolute -right-20 -top-24 h-72 w-72 rounded-full bg-sky-500/20 blur-3xl"
        aria-hidden="true"
      />
      <div
        class="pointer-events-none absolute -bottom-28 -left-16 h-72 w-72 rounded-full bg-sky-600/10 blur-3xl"
        aria-hidden="true"
      />

      <div class="relative mx-auto max-w-6xl px-4 py-16 sm:px-6 sm:py-24">
        <span
          class="inline-flex items-center gap-2 rounded-full bg-white/10 px-3 py-1 text-xs font-semibold uppercase tracking-widest text-sky-300 ring-1 ring-inset ring-white/10"
        >
          Academic Year 2025–2026
        </span>

        <h1 class="mt-6 max-w-2xl text-3xl font-bold tracking-tight sm:text-5xl">
          Student Information
          <span class="text-sky-400">Portal</span>
        </h1>

        <p class="mt-4 max-w-xl text-sm leading-relaxed text-slate-300 sm:text-base">
          A clean, responsive showcase of reusable Vue components and props for the
          BS Information Technology program at Caraga State University.
        </p>

        <div class="mt-8 flex flex-wrap gap-3">
          <AppButton label="Browse Students" color="primary" to="/students" />
          <AppButton label="Portal Overview" color="slate" @click="scrollToOverview" />
        </div>
      </div>
    </section>

    <!-- Overview / InfoCards -->
    <section id="overview" class="mx-auto max-w-6xl scroll-mt-24 px-4 py-14 sm:px-6">
      <div class="max-w-2xl">
        <p class="text-xs font-bold uppercase tracking-widest text-sky-600">Overview</p>
        <h2 class="mt-2 text-2xl font-bold tracking-tight text-slate-900 sm:text-3xl">
          Everything in one portal
        </h2>
        <p class="mt-3 text-sm leading-relaxed text-slate-600 sm:text-base">
          This website demonstrates how small, focused Vue components can be composed into a
          complete site through shared layouts and props.
        </p>
      </div>

      <div class="mt-8 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <InfoCard
          title="Portal Overview"
          description="A centralized hub for viewing student records, enrollment status, and program details in a single, easy-to-navigate interface."
        />
        <InfoCard
          title="Enrollment Guidelines"
          description="Review prerequisites, filing periods, and checklist items before enrolling. Keep your student ID handy for verification."
        />
        <InfoCard
          title="Component Architecture"
          description="Built from reusable components — AppHeader, AppFooter, StudentCard, InfoCard, and AppButton — all powered by Vue props."
        />
      </div>
    </section>

    <!-- AppButton variants -->
    <section class="border-y border-slate-200 bg-white">
      <div class="mx-auto max-w-6xl px-4 py-14 sm:px-6">
        <div class="max-w-2xl">
          <p class="text-xs font-bold uppercase tracking-widest text-sky-600">AppButton</p>
          <h2 class="mt-2 text-2xl font-bold tracking-tight text-slate-900 sm:text-3xl">
            Button variants
          </h2>
          <p class="mt-3 text-sm leading-relaxed text-slate-600">
            The <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >AppButton</code>
            component accepts a <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >label</code>, a <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >color</code> prop (<code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >primary</code>, <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >secondary</code>, <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >emerald</code>, <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >rose</code>, <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >slate</code>), and an optional <code
              class="rounded bg-slate-100 px-1.5 py-0.5 text-xs font-semibold text-slate-700"
            >to</code> for router links.
          </p>
        </div>

        <div class="mt-8 flex flex-wrap gap-3">
          <AppButton label="Open Directory" color="primary" to="/students" />
          <AppButton label="Secondary" color="secondary" @click="showAction('Secondary action triggered')" />
          <AppButton label="Approve" color="emerald" @click="showAction('Approved!')" />
          <AppButton label="Delete" color="rose" @click="showAction('Delete action triggered')" />
          <AppButton label="Cancel" color="slate" @click="showAction('Cancelled')" />
        </div>

        <p class="mt-4 text-sm text-slate-500" aria-live="polite">
          <template v-if="lastAction">
            Last action:
            <span class="font-semibold text-slate-700">{{ lastAction }}</span>
          </template>
          <template v-else>
            Click a button to see its click event in action.
          </template>
        </p>
      </div>
    </section>

    <!-- Featured students -->
    <section class="mx-auto max-w-6xl px-4 py-14 sm:px-6">
      <div class="flex flex-wrap items-end justify-between gap-4">
        <div class="max-w-xl">
          <p class="text-xs font-bold uppercase tracking-widest text-sky-600">StudentCard</p>
          <h2 class="mt-2 text-2xl font-bold tracking-tight text-slate-900 sm:text-3xl">
            Featured students
          </h2>
          <p class="mt-3 text-sm leading-relaxed text-slate-600">
            Each card is driven entirely by props: name, studentId, program, yearLevel, status,
            and avatarColor.
          </p>
        </div>
        <AppButton label="View All Students" color="rose" to="/students" />
      </div>

      <div class="mt-8 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <StudentCard
          v-for="student in featuredStudents"
          :key="student.studentId"
          :name="student.name"
          :student-id="student.studentId"
          :program="student.program"
          :year-level="student.yearLevel"
          :status="student.status"
          :avatar-color="student.avatarColor"
        />
      </div>
    </section>
  </div>
</template>
