<script setup lang="ts">
useHead({ title: 'Students | Student Information Website' })

type YearFilter = 'All' | '1st Year' | '2nd Year' | '3rd Year' | '4th Year'

const students = [
  {
    name: 'Maria Santos',
    studentId: '2024-IT-0117',
    program: 'BS Information Technology',
    yearLevel: '1st Year',
    status: 'Regular',
    avatarColor: '#0284c7',
  },
  {
    name: 'Juan Dela Cruz',
    studentId: '2024-IT-0233',
    program: 'BS Information Technology',
    yearLevel: '1st Year',
    status: 'Regular',
    avatarColor: '#7c3aed',
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
    name: 'Paolo Mendoza',
    studentId: '2023-IT-0089',
    program: 'BS Information Technology',
    yearLevel: '2nd Year',
    status: 'Transferee',
    avatarColor: '#db2777',
  },
  {
    name: 'Bea Villanueva',
    studentId: '2022-IT-0561',
    program: 'BS Information Technology',
    yearLevel: '3rd Year',
    status: 'Regular',
    avatarColor: '#059669',
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

const filters: Array<{ label: YearFilter; color: 'primary' | 'secondary' | 'emerald' | 'rose' | 'slate' }> = [
  { label: 'All', color: 'primary' },
  { label: '1st Year', color: 'secondary' },
  { label: '2nd Year', color: 'emerald' },
  { label: '3rd Year', color: 'rose' },
  { label: '4th Year', color: 'slate' },
]

const activeFilter = ref<YearFilter>('All')

const filteredStudents = computed(() =>
  activeFilter.value === 'All'
    ? students
    : students.filter(student => student.yearLevel === activeFilter.value),
)
</script>

<template>
  <div class="mx-auto max-w-6xl px-4 py-10 sm:px-6 sm:py-14">
    <!-- Summary banner -->
    <InfoCard
      class="mb-8"
      title="Students Directory"
      description="A live summary of the BS Information Technology student body at Caraga State University. Use the year-level filters below to browse — 6 enrolled records across four levels."
    />

    <!-- Heading + filters -->
    <div class="flex flex-col gap-4 sm:flex-row sm:items-end sm:justify-between">
      <div>
        <h1 class="text-2xl font-bold tracking-tight text-slate-900 sm:text-3xl">All Students</h1>
        <p class="mt-1 text-sm text-slate-500">
          Showing
          <span class="font-semibold text-slate-700">{{ filteredStudents.length }}</span>
          of {{ students.length }} students
          <template v-if="activeFilter !== 'All'"> · {{ activeFilter }}</template>
        </p>
      </div>

      <div class="flex flex-wrap gap-2" role="group" aria-label="Filter students by year level">
        <AppButton
          v-for="filter in filters"
          :key="filter.label"
          :label="activeFilter === filter.label ? `✓ ${filter.label}` : filter.label"
          :color="filter.color"
          :class="
            activeFilter === filter.label
              ? 'ring-2 ring-sky-500 ring-offset-2 ring-offset-slate-50'
              : ''
          "
          @click="activeFilter = filter.label"
        />
      </div>
    </div>

    <!-- Students grid -->
    <div
      v-if="filteredStudents.length > 0"
      class="mt-8 grid gap-6 sm:grid-cols-2 lg:grid-cols-3"
    >
      <StudentCard
        v-for="student in filteredStudents"
        :key="student.studentId"
        :name="student.name"
        :student-id="student.studentId"
        :program="student.program"
        :year-level="student.yearLevel"
        :status="student.status"
        :avatar-color="student.avatarColor"
      />
    </div>

    <!-- Empty state -->
    <div
      v-else
      class="mt-8 rounded-2xl border border-dashed border-slate-300 bg-white p-10 text-center"
    >
      <p class="text-sm font-medium text-slate-600">
        No students found for this filter.
      </p>
    </div>
  </div>
</template>
