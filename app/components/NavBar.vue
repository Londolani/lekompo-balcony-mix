<!-- components/NavBar.vue -->

<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const items: NavigationMenuItem[] = [
  { label: 'Home', to: '#hero', icon: 'i-lucide-home' },
  { label: 'Events', to: '#events', icon: 'i-lucide-calendar' },
  { label: 'About', to: '#about', icon: 'i-lucide-info' },
  { label: 'Artists', to: '#artists', icon: 'i-lucide-users' },
  { label: 'Music', to: '#music', icon: 'i-lucide-music' },
  { label: 'Gallery', to: '#gallery', icon: 'i-lucide-image' }
]
</script>

<template>
  <div class="fixed top-0 w-full bg-black z-50 shadow-lg">
    <UNavigationMenu
      :items="items"
      class="w-full justify-around px-4 py-3"
      orientation="horizontal"
      variant="link"
      highlight
      highlight-color="primary"
    >
      <template #default="{ item }: { item: NavigationMenuItem }">
        <NuxtLink
          :to="item.to"
          class="flex items-center bg-black text-red-500 hover:text-yellow-400 transition-all duration-300 px-4 py-2 rounded"
        >
          <i :class="item.icon + ' mr-2'" />
          {{ item.label }}
        </NuxtLink>
      </template>
    </UNavigationMenu>
  </div>
</template>

<!-- pages/index.vue -->
<!-- Unchanged: leave the rest of the one-page layout as-is until nav is finalized -->
