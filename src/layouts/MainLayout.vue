<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          {{ $t('Bot Controler') }}
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> {{ $t('Main Menu') }} </q-item-label>

        <StandardLink v-for="link in links" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import StandardLink from 'src/components/StandardLink.vue';
import { defineComponent, ref } from 'vue';

const linksList = [
  {
    title: 'Home',
    caption: 'Main page',
    icon: 'home',
    link: '/',
  },
];

export default defineComponent({
  name: 'MainLayout',

  components: {
    StandardLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      links: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
