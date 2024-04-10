<template>
  <v-app :theme="themeToggle">
    <NavigationDrawer />
    <AppBar @toogleTheme="event" />
    <v-main>
      <v-container>
        <NameInput />
        <ModalUser />
        <v-row>
          <CardTemplate />
        </v-row>
      </v-container>
    </v-main>
    <AppFooter />
  </v-app>
</template>

<script setup>

  import { ref } from 'vue';
  import NavigationDrawer from '@/components/NavigationDrawer.vue';
  import AppBar from './components/AppBar.vue';
  import NameInput from './components/NameInput.vue';
  import ModalUser from './components/modal/ModalUser.vue';
  import CardTemplate from './components/CardTemplate.vue';

  var themeToggle = ref('light')

  const event = (theme) => {
    themeToggle.value = theme
  }

</script>

