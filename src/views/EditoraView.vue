<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      nova_editora: "",
      editoras: [
        {
          id: "ac803529-5e2d-45b2-a907-ca993bb301ea",
          name: "Arco iris",
        },
        {
          id: "f0532191-04bb-44fe-be8b-8449ce321169",
          name: "Azul",
        },
        {
          id: "29eaba8d-a376-485e-9509-5dddd6587f0d",
          name: "Rocco",
        },
        {
          id: "d7c068f0-928f-4858-9ae3-eadc32edb230",
          name: "Página",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.nova_editora !== "") {
        const novo_id = uuid();
        this.editoras.push({
          id: novo_id,
          name: this.nova_editora,
        });
        this.nova_editora = "";
      }
    },
    excluir(editora) {
      const indice = this.editoras.indexOf(editora);
      this.editoras.splice(indice, 1);
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
      <h2>Gerencimento de Editoras</h2>
    </div>
    <div class="input-form">
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
            <td>Editoras</td>
            <td>Ações</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="editora in editoras" :key="editora.id">
            <td>{{ editora.id }}</td>
            <td>{{ editora.name }}</td>
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
