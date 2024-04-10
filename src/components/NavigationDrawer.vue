<template>
  <v-navigation-drawer v-model="isToogleBar">
    <v-list>
      <v-list-subheader>Menu</v-list-subheader>

      <v-list-group value="Perfil">
        <template #activator="{ props }">
          <v-list-item v-bind="props" prepend-icon="mdi-account-circle" title="Perfil"></v-list-item>
        </template>
        <v-list-item href="#home">Ver Perfil</v-list-item>
        <v-list-item href="#home">Ver comentários</v-list-item>
        <v-list-item href="#home">Sair</v-list-item>
      </v-list-group>

      <v-list-item prepend-icon="mdi-home" href="#home">Home</v-list-item>
      <v-list-item prepend-icon="mdi-account" href="#home">Usuários</v-list-item>
      <v-list-item prepend-icon="mdi-comment" href="#home">Comentários</v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script setup>
  import EventBus from '../../eventBus';
  import { ref } from 'vue'

  var isToogleBar = ref(false);
  
  EventBus.on((toogleBar) => {
    isToogleBar.value = toogleBar;
  })

</script>