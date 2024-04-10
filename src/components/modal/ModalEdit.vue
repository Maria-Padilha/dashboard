<template>
    <v-btn @click="dialog = !dialog" variant="tonal">Editar</v-btn>
    <v-dialog width="600px" v-model="dialog">
        <v-card>
            <v-card-title>Editar Usuário</v-card-title>
            <v-card-text>
              <v-row>
                <v-col>
                  <v-text-field label="Nome" variant="solo-filled"></v-text-field>
                </v-col>
                <v-col>
                  <v-text-field label="E-mail" variant="solo-filled"></v-text-field>
                </v-col>
              </v-row>
              <v-select label="Cargo" variant="solo-filled" :items="['Admin','Usuário', 'Visitante']"></v-select>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn @click="dialog = false">Cancelar</v-btn>
                <v-btn variant="tonal">Salvar</v-btn>
              </v-card-actions>
            </v-card-text>
          </v-card>
    </v-dialog>
</template>

<script setup>
    import { ref } from 'vue';
    const dialog = ref(false)
</script>