<template>
    <v-btn @click="dialog = !dialog" class="grey-darken-2" variant="tonal" prepend-icon="mdi-comment">Comentar</v-btn>
    <v-dialog width="600px" v-model="dialog">
        <v-card>
            <v-card-title>Comentar</v-card-title>
            <v-card-text>
                <v-row>
                    <v-col>
                        <v-text-field label="Nome" variant="solo-filled"></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <v-textarea label="Comentário" variant="solo-filled"></v-textarea>
                    </v-col>
                </v-row>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn @click="dialog = false">Cancelar</v-btn>
                    <v-btn variant="tonal">Enviar</v-btn>
                </v-card-actions>
            </v-card-text>
        </v-card>
    </v-dialog>
</template>

<script setup>
    import { ref } from "vue";
    const dialog = ref(false)
</script>