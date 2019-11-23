<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          v-if="$route.fullPath.includes('/chat')"
          v-go-back.single
          flat
          dense
          icon="arrow_back"
          label="Back"
        />
        <q-toolbar-title class="absolute-center">
          {{ title }}
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MyLayout',
  computed: {
    title() {
      const currentPath = this.$route.fullPath
      if (currentPath === '/') return 'SmallChat'
      else if (currentPath === '/chat') return 'Chat'
      else if (currentPath === '/auth') return 'Login'
    },
  },
  data() {
    return {
      leftDrawerOpen: false,
    }
  },
}
</script>
