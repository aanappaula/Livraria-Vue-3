<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_autor: "",
      nova_categoria: "",
      nova_editora: "",
      autores: [
        {
          id: "ac803529-5e2d-45b2-a907-ca993bb301ea",
          autor: "J.K Rowling",
          categoria: "Romance",
          editora: "Azul",
        },
        {
          id: "f0532191-04bb-44fe-be8b-8449ce321169",
          autor: "Carlos Ruíz Zafón",
          categoria: "Romance",
          editora: "Rocco",
        },
        {
          id: "29eaba8d-a376-485e-9509-5dddd6587f0d",
          autor: "Khaled Hosseini",
          categoria: "Terror",
          editora: "Página",
        },
        {
          id: "d7c068f0-928f-4858-9ae3-eadc32edb230",
          autor: "Sidney Sheldon",
          categoria: "Suspense",
          editora: "Arcoíris",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_autor !== "") {
        const novo_id = uuid();
        this.autores.push({
          id: novo_id,
          autor: this.novo_autor,
          categoria: this.nova_categoria,
          editora: this.nova_editora,
        });
        this.novo_autor = "";
        this.nova_categoria = "";
        this.nova_editora = "";
      }
    },
    excluir(autor) {
      const indice = this.autores.indexOf(autor);
      this.autores.splice(indice, 1);
    },
    alerta() {
      alert("ok");
    },
  },
};
</script>

<template>
  <main>
    <div class="conteudo">
      <div class="titulo">
        <h2>Gerencimento de Autores</h2>
      </div>
      <div class="input-form">
        <input
          type="text"
          v-model="novo_autor"
          @keyup.enter="salvar"
          placeholder="Autores"
        />
        <input
          type="text"
          v-model="nova_categoria"
          @keyup.enter="salvar"
          placeholder="Categorias"
        />
        <input
          type="text"
          v-model="nova_editora"
          @keyup.enter="salvar"
          placeholder="Editoras"
        />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="itens-lista">
        <table>
          <thead>
            <tr>
              <td>ID</td>
              <td>Autores</td>
              <td>Categorias</td>
              <td>Editoras</td>
              <td>Ações</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="autor in autores" :key="autor.id">
              <td>{{ autor.id }}</td>
              <td>{{ autor.autor }}</td>
              <td>{{ autor.categoria }}</td>
              <td>{{ autor.editora }}</td>
              <td>
                <button class="botao" @click="alerta">Editar</button>
                <button class="botao" @click="excluir">Excluir</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </main>
</template>

<style scoped>
template {
  height: 70%;
}
</style>
