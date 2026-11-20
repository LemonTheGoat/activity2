<template>
  <div class="flex min-h-screen flex-col bg-slate-50 font-sans text-slate-800 antialiased">
    <AppHeader />

    <main class="flex-1">
      <slot />
    </main>

    <AppFooter />
  </div>
</template>
