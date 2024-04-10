<template>
    <v-table>
      <thead>
        <tr>
          <th>Nome</th>
          <th>E-mail</th>
          <th>Cargo</th>
          <th>Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users_db" :key="user.id">
          <td>{{ user.name_user }}</td>
          <td>{{ user.email_user }}</td>
          <td>{{ user.office_user }}</td>
          <td>
            <ModalEdit />
          </td>
        </tr>
      </tbody>
    </v-table>
</template>

<script setup>
  import { ref, onMounted } from 'vue';
  import ModalEdit from './modal/ModalEdit.vue';

  const users_db = ref(null);

  async function getUsers(){
    const req = await fetch("http://localhost:5000/Usuarios");
    const data = await req.json()
    users_db.value = data;
  }

  onMounted(() => {
    getUsers()
  })
</script>