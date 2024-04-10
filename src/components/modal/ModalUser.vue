<template>

  <v-card class="mb-5">
    <v-alert v-model="alert" closable text="Usuário cadastrado!" type="success" variant="tonal"></v-alert>
    <div class="d-flex justify-space-between">
      <v-card-title>Últimos usuários</v-card-title>
      <v-card-title>
        <v-btn @click="dialog = !dialog" icon="mdi-plus"></v-btn>
        <v-form @submit.prevent="createUser" id="createUser">
          <v-dialog width="700px" v-model="dialog">
            <v-card>
              <v-card-title>Adicionar Usuário</v-card-title>
              <v-card-text>
                <v-row>
                  <v-col>
                    <v-text-field v-model="name" :rules="nameRules" label="Nome" variant="solo-filled"></v-text-field>
                  </v-col>
                  <v-col>
                    <v-text-field v-model="email" :rules="emailRules" label="E-mail" variant="solo-filled"></v-text-field>
                  </v-col>
                </v-row>
                <v-select v-model="office" :rules="[v => !!v || 'O cargo é obrigatório']" required label="Cargo" variant="solo-filled" :items="['Administrador','Usuário','Visitante']"></v-select>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn @click="dialog = false">Cancelar</v-btn>
                  <v-btn variant="tonal" type="submit" text="Enviar" form="createUser"></v-btn>
                </v-card-actions>
              </v-card-text>
            </v-card>
          </v-dialog>
        </v-form>
      </v-card-title>
    </div>

    <UserTable />
  </v-card>
</template>

<script setup>
    // importando arquivos
    import { ref, defineAsyncComponent, onMounted } from 'vue';
    import UserTable from '../UserTable.vue'

    const dialog = ref(false)
    const alert = ref(false)

    // validação do forms
    const emailRules = [
    value => {
      if(value) return true;
      return 'O email é obrigatório'
    },
    value => {
      if(value.includes('@')) return true;
      return 'O formato de e-mail não é válido'
    }
  ]

  const nameRules = [
    value => {
      if(value) return true;
      return 'O nome é obrigatório'
    }
  ]

  const name = ref(null);
  const email = ref(null);
  const office = ref(null);

  // criando usuários
  async function createUser(){

    dialog.value = false
    alert.value = true

    const data = {
      name_user: name.value,
      email_user: email.value,
      office_user: office.value 
    }

    const dataJson = JSON.stringify(data);

    const req = await fetch("http://localhost:5000/Usuarios", {
      method: "POST", 
      headers: {"Content-Type":"application/json"}, 
      body: dataJson
    })

    const res = await req.json();
    
  }

  onMounted(() => {
    
  })

</script>