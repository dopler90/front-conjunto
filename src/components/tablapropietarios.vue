<template>
    <div class="tbpropietario">
      <fieldset>
        <legend>Tabla de propietarios</legend>
        <table>
          <tr>
            <th>id</th>
            <th>nombre</th>
            <th>usuario</th>
            <th>contrasena</th>
            <th>documento</th>
            <th>telefono</th>
            <th>email</th>
            <th>persona</th>
            <th>cuenta</th>
          </tr>
          <tr v-for="propietario in propietarios" :key="propietario.id_propietario">
            <td>{{ propietario.id_propietario }}</td>
          <td>{{ propietario.nombre }}</td>
          <td>{{ propietario.usuario }}</td>
          <td>{{ propietario.contrasena }}</td>
          <td>{{ propietario.documento }}</td>
          <td>{{ propietario.telefono }}</td>
          <td>{{ propietario.email }}</td>
          <td>{{ propietario.persona }}</td>
          <td>{{ propietario.cuenta }}</td>
          </tr>
         
        </table>
      </fieldset>
  
      
    </div>
  </template>
  
  <script>
  export default {
  name: "tabla-propietarios",
  props: {
    propietarios: {
      type: Array,
    }
  },
  methods: {},
};
</script>

<style scoped>
.tbpropietario {
  padding: 5%;
  text-align: center;
}
table {
  border: 1px solid #000;
  margin: auto;
  padding: 1 px;
}
th {
  border: 1px solid #000;
}
tr,
td {
  width: 20%;
  text-align: left;
  vertical-align: top;
  border: 1px solid #000;
}
</style>