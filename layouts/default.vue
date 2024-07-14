<script setup lang="ts">
interface INavDrawerLinks {
  title: string
  icon: string
  value: string
  link: string
}

const navigationDrawerLinks = ref<INavDrawerLinks[]>([
  { title: 'Inicio', icon: 'mdi-home-city', value: 'index', link: '/' },
  { title: 'Membros', icon: 'mdi-account-group-outline', value: 'members', link: '/membros' },
])
</script>

<template>
  <div>
    <v-app-bar :elevation="0" class="bg-black">
      <v-app-bar-title>Application Bar</v-app-bar-title>
      <template v-slot:append>
        <!-- TODO: ICON FOR SEARCH MEMBERS -->
        <v-btn icon="mdi-magnify"></v-btn>
        <!-- TODO: ICON TO LOGOUT -->
        <v-btn icon="mdi-dots-vertical"></v-btn>
      </template>
    </v-app-bar>

    <v-navigation-drawer permanent>
      <v-list density="compact" nav class="mt-4">
        <v-list-item 
          v-for="(link, linkIndex) in navigationDrawerLinks" 
          :key="`item-${linkIndex}`"
          :prepend-icon="link.icon" 
          :title="link.title" 
          :value="link.value" 
          @click="navigateTo(link.link)"
        />
      </v-list>
    </v-navigation-drawer>

    <main class="d-flex flex-column mt-16">
      <NuxtPage />
    </main>
  </div>
</template>