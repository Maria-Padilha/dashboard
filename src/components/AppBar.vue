<template>
    <v-app-bar flat class="border-b">
      <v-app-bar-nav-icon @click="isDrawerOpen"></v-app-bar-nav-icon>
      <v-app-bar-title>Dashboard</v-app-bar-title>
    
      <template #append>
        <v-btn icon @click="toogleTheme">
          <v-icon icon="mdi-brightness-6" class="grey-darken-4"></v-icon>
        </v-btn>
        <v-btn icon class="mr-2">
          <v-badge dot color="info">
            <v-icon icon="mdi-bell-outline"></v-icon>
          </v-badge>
        </v-btn>
        <v-avatar>
          <v-img src="@/assets/img/perfil.jpg" cover alt="alt"></v-img>
        </v-avatar>
      </template>
    </v-app-bar>
</template>

<script setup>
  
  import { ref, defineEmits } from 'vue';
  import EventBus from '../../eventBus';
  
  
  const emit = defineEmits(['toogleTheme', 'isDrawerOpen'])

  var toogleBar = ref(false);
  const isDrawerOpen = () => {
    toogleBar.value = true
    EventBus.emit(toogleBar.value)
  }

  var theme = ref('light');
  var mode = ref(true)

  const toogleTheme = () => {
    mode.value = !mode.value;
    theme.value = mode.value ? "light" : "dark";
    emit('toogleTheme', theme.value)
  }
 
</script>