<template>
    <div class="formpropietario">
      <fieldset>
        <legend>Registro Propietarios</legend>
        <form @submit.prevent="guardar">
            <label for="id_propietario">id_propietario</label><br />
          <input
            type="number"
            name="id_propietario"
            id="id_propietario"
            v-model="propietario.id_propietario"
          /><br />
  
          <label for="nombre">nombre</label><br />
          <input
            type="text"
            name="nombre"
            id="nombre"
            v-model="propietario.nombre"
          /><br />
  
          <label for="usuario">usuario</label><br />
          <input
            type="text"
            name="usuario"
            id="usuario"
            v-model="propietario.usuario"
          /><br />

          <label for="contrasena">contrasena</label><br />
          <input
            type="text"
            name="contrasena"
            id="contrasena"
            v-model="propietario.contrasena"
          /><br />

          <label for="documento">documento</label><br />
          <input
            type="text"
            name="documento"
            id="documento"
            v-model="propietario.documento"
          /><br />

          <label for="telefono">telefono</label><br />
          <input
            type="text"
            name="telefono"
            id="telefono"
            v-model="propietario.telefono"
          /><br />

          <label for="email">email</label><br />
          <input
            type="text"
            name="email"
            id="email"
            v-model="propietario.email"
          /><br />

          <label for="persona">persona</label><br />
          <input
            type="text"
            name="persona"
            id="persona"
            v-model="propietario.persona"
          /><br />

          <label for="cuenta">cuenta</label><br />
          <input
            type="text"
            name="cuenta"
            id="cuenta"
            v-model="propietario.cuenta"
          /><br />
  
          <button type="submit">Guardar</button>
          <button type="button" @click="eliminar(propietario.id_propietario)">
            Eliminar
          </button>
        </form>
      </fieldset>
      <router-view />
    </div>
  </template>
  
  <script>
  import axios from "axios";
  export default {
    name: "formulario-propietarios",
    data: function () {
      return {
        propietario: {
          id_propietario: "",
          nombre: "",
          usuario: "",
          contrasena: "",
          documento: "",
          telefono: "",
          email: "",
          persona: "",
          cuenta: "",
        },
      };
    },
    methods: {
      guardar() {
        axios
          .post("http://localhost:9090/api/propietario", this.propietario)
          .then((data) => {
            console.log("response", data);
            this.$emit("refresh");
          });
      },
      eliminar(id) {
        axios
          .delete("http://localhost:9090/api/propietario/" + id)
          .then((data) => {
            console.log("response", data);
            this.propietario.id_propietario = null;
            this.$emit("refresh");
          })
          .catch(() => {
            alert("El propietario seleccionado no existe");
          });
        console.log(id);
      },
    },
  };
  </script>
  
  
  
  <style scoped>
  .formpropietario {
    text-align: center;
    padding: 5%;
    font-family: inherit;
  }
  </style>