<template>
    <div class="propietario">
      <h1>Esta es la vista propietarios</h1>
      <formulariopropietarios @refresh="refrescar"/>
      <tablapropietarios :propietarios="propietarios"/>
    </div>
  </template>

<script>

import tablapropietarios from '@/components/tablapropietarios.vue'
import formulariopropietarios from '@/components/formulariopropietarios.vue'
import axios from "axios";

export default {
  name: "propietarios-view",
  components: {
    formulariopropietarios,
    tablapropietarios,
  },
  data: () => ({
    propietarios: [],
  }),
  mounted() {
    this.getpropietarios();
  },
  methods: {
    refrescar() {
      this.getpropietarios();
    },
    getpropietarios() {
      axios
        .get("http://localhost:9090/api/propietario/listar")
        .then((response) => {
          this.propietarios = response.data;
        });
    },
  },
};
</script>

<style scoped>
.propietario {
  text-align: center;
}
</style>