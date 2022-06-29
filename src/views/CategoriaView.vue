<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      nova_categoria: "",
      nova_editora: "",
      categorias: [
        {
          id: "ac803529-5e2d-45b2-a907-ca993bb301ea",
          categoria: "Romance",
          editora: "Azul",
        },
        {
          id: "f0532191-04bb-44fe-be8b-8449ce321169",
          categoria: "Romance",
          editora: "Rocco",
        },
        {
          id: "29eaba8d-a376-485e-9509-5dddd6587f0d",
          categoria: "Terror",
          editora: "Página",
        },
        {
          id: "d7c068f0-928f-4858-9ae3-eadc32edb230",
          categoria: "Suspense",
          editora: "Arcoíris",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.nova_categoria !== "") {
        const novo_id = uuid();
        this.categorias.push({
          id: novo_id,
          categoria: this.nova_categoria,
          editora: this.nova_editora,
        });
        this.nova_categoria = "";
        this.nova_editora = "";
      }
    },
    excluir(categoria) {
      const indice = this.categorias.indexOf(categoria);
      this.categorias.splice(indice, 1);
    },
    alerta() {
      alert("ok");
    },
  },
};
</script>

<template>
  <div class="conteudo">
    <div class="titulo">
      <h2>Gerencimento de Categorias</h2>
    </div>
    <div class="input-form">
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
            <td>Categorias</td>
            <td>Editoras</td>
            <td>Ações</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="categoria in categorias" :key="categoria.id">
            <td>{{ categoria.id }}</td>
            <td>{{ categoria.categoria }}</td>
            <td>{{ categoria.editora }}</td>
            <td>
              <button class="botao" @click="alerta">Editar</button>
              <button class="botao" @click="excluir">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style></style>
