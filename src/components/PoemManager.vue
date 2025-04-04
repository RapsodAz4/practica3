<template>
    <div>
      <h1>Gestor de Poemas</h1>
      <form @submit.prevent="addPoem">
        <input v-model="newPoem.title" placeholder="Título del poema" required />
        <button type="submit">Agregar Poema</button>
      </form>
  
      <ul>
        <li v-for="(poem, index) in poems" :key="index">
          <span>{{ poem.title }}</span>
          <button @click="editPoem(index)">Editar</button>
          <button @click="deletePoem(index)">Eliminar</button>
        </li>
      </ul>
  
      <div v-if="editingIndex !== null">
        <h2>Editar Poema</h2>
        <input v-model="editedPoem.title" placeholder="Título del poema" required />
        <button @click="updatePoem">Actualizar</button>
        <button @click="cancelEdit">Cancelar</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newPoem: {
          title: ''
        },
        poems: [],
        editingIndex: null,
        editedPoem: {
          title: ''
        }
      };
    },
    methods: {
      addPoem() {
        this.poems.push({ title: this.newPoem.title });
        this.newPoem.title = '';
      },
      editPoem(index) {
        this.editingIndex = index;
        this.editedPoem = { ...this.poems[index] };
      },
      updatePoem() {
        this.$set(this.poems, this.editingIndex, this.editedPoem);
        this.cancelEdit();
      },
      deletePoem(index) {
        this.poems.splice(index, 1);
      },
      cancelEdit() {
        this.editingIndex = null;
        this.editedPoem = { title: '' };
      }
    }
  };
  </script>
  
  
<style scoped>
body {
  font-family: 'Arial', sans-serif;
  background: linear-gradient(135deg, #42b883, #35495e);
  color: white;
  margin: 0;
  padding: 20px;
  text-align: center;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

form {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
  flex-direction: column;
  align-items: center;
}

input {
  padding: 10px;
  border: none;
  border-radius: 5px;
  margin-right: 10px;
  width: 300px;
  font-size: 16px;
  transition: all 0.3s ease;
  margin-bottom: 10px;
}

input:focus {
  outline: none;
  box-shadow: 0 0 5px rgba(66, 184, 131, 0.7);
}

button {
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  background-color: #2889f1;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #042022;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  background: rgba(255, 255, 255, 0.1);
  margin: 10px 0;
  padding: 15px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: background 0.3s ease;
}

li:hover {
  background: rgba(255, 255, 255, 0.2);
}

h2 {
  margin-top: 20px;
  text-align: center;
}

.edit-container {
  margin-top: 20px;
  text-align: center;
}
</style>


  