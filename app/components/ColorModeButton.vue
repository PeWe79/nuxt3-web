<script setup>
const colorMode = useColorMode()

const isDark = computed({
  get() {
    return colorMode.value === 'dark'
  },
  set() {
    colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
  },
})
</script>

<template>
  <ClientOnly v-if="!colorMode?.forced">
    <button :icon="isDark ? 'i-lucide-moon' : 'i-lucide-sun'" color="neutral" variant="ghost" @click="isDark = !isDark">
      <Icon v-if="$colorMode.value === 'light'" name="heroicons:sun" class="h-7 w-7 text-zinc-700 dark:text-zinc-300" aria-hidden="true" />
      <Icon v-else="$colorMode.value === 'dark'" name="heroicons:moon" class="h-7 w-7 text-zinc-700 dark:text-zinc-300" aria-hidden="true" />
    </button>

    <template #fallback>
      <div class="size-8" />
    </template>
  </ClientOnly>
</template>
