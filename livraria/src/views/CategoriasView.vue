<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      categorias: [
        { id: "Arte", nome: "2 anos" },
        { id: "Bíblia", nome: " 14 anos" },
        { id: "Biografias", nome: "Gênero D" },
        { id: "Ciências Biológicas", nome: "Gênero E" },
        { id: "Didáticos", nome: "Gênero F" },
        { id: "Direito", nome: "Gênero G" },
        { id: "Ficção Ciêntifíca", nome: "Gênero H" },        
        { id: "Informática", nome: "Gênero I" },
        { id: "Romances", nome: "Gênero I" },
        { id: "Suspense e Terror", nome: "Gênero I" },



      ],
      nova_categoria: "",
    };
  },

  methods: {
    salvar() {
      if (this.nova_categoria !== "") {
        const novo_id = uuidv4();
        this.categorias.push({
          id: novo_id,
          nome: this.nova_categorias,
        });
        this.nova_categoria = "";
      }
    },
    excluir(categorias) {
      const indice = this.categorias.indexOf(categorias);
      this.categorias.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Categorias</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="nova_categoria" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-categorias">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Classificação</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="categorias in categorias" :key="categorias.id">
            <td>{{ categorias.id }}</td>
            <td>{{ categorias.nome }}</td>
            <td>
              <button @click="excluir(categorias)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
.title {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}
.form-input {
  margin-top: 10px;
  display: flex;
  justify-content: center;
}

.form-input input {
  width: 60%;
  height: 40px;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 0 10px;
}

.form-input button {
  margin-left: 1%;
  width: 20%;
  height: 40px;
  border: 1px solid rgb(0, 0, 0);
  border-radius: 10px;
  background-color: rgb(0, 0, 0);
  color: white;
  font-weight: bold;
  cursor: pointer;
}

.list-categorias {
  display: flex;
  justify-content: center;
}

table {
  width: 50%;
  margin: 2% auto;
  border-collapse: collapse;
}

table tr th {
  border: 1px solid #ccc;
  padding: 10px;
  font-weight: bold;
}

table tr td {
  border: 1px solid #ccc;
  padding: 10px;
}

table tr:nth-child(odd) {
  background-color: black;
}
</style>
