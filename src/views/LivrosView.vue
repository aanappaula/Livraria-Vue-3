<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_livro: "",
      novo_autor: "",
      nova_categoria: "",
      nova_editora: "",
      livros: [
        {
          id: "ac803529-5e2d-45b2-a907-ca993bb301ea",
          nome_livro: "Harry Potter e a Pedra  Filosofal",
          autor: "J.K Rowling",
          categoria: "Romance",
          editora: "Azul",
        },
        {
          id: "f0532191-04bb-44fe-be8b-8449ce321169",
          nome_livro: "A sombra do vento",
          autor: "Carlos Ruíz Zafón",
          categoria: "Terror",
          editora: "Rocco",
        },
        {
          id: "29eaba8d-a376-485e-9509-5dddd6587f0d",
          nome_livro: "O caçador de pipas",
          autor: "Khaled Hosseini",
          categoria: "Mistério",
          editora: "Página",
        },
        {
          id: "d7c068f0-928f-4858-9ae3-eadc32edb230",
          nome_livro: "Anjo da escuridão",
          autor: "Sidney Sheldon",
          categoria: "Suspense",
          editora: "Arcoíris",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_livro !== "") {
        const novo_id = uuid();
        this.livros.push({
          id: novo_id,
          nome_livro: this.novo_livro,
          autor: this.novo_autor,
          categoria: this.nova_categoria,
          editora: this.nova_editora,
        });
        this.novo_livro = "";
        this.novo_autor = "";
        this.nova_categoria = "";
        this.nova_editora = "";
      }
    },
    excluir(livro) {
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
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
      <h2>Gerencimento de Livros</h2>
    </div>
    <div class="input-form">
      <input
        type="text"
        v-model="novo_livro"
        @keyup.enter="salvar"
        placeholder="Livros"
      />
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
            <td>Livros</td>
            <td>Autores</td>
            <td>Categorias</td>
            <td>Editoras</td>
            <td>Ações</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.nome_livro }}</td>
            <td>{{ livro.autor }}</td>
            <td>{{ livro.categoria }}</td>
            <td>{{ livro.editora }}</td>

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
