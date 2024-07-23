<template>
  <div>
    <h1>Lista de Departamentos</h1>
    <center>
    <table class="mi-tabla">
      <tr>
        <th>Nombre completo</th>
        <th>Costo departamento</th>
        <th>Numero cuartos</th>
        <th>Edificio</th>
      </tr>
      <tr v-for="t in departamentos" :key="t.id">
        <td>{{ t.nombre_completo_propietario }}</td>
        <td>{{ t.costo_departamento }}</td>
        <td>{{ t.numero_cuartos }}</td>
        <td>{{ t.edificio }}</td>
      </tr>
    </table>
    </center>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      departamentos: []
    };
  },
  created() {
    this.fetchDepartamentos();
  },
  methods: {
    async fetchDepartamentos() {
      try {
        const response = await axios.get('http://127.0.0.1:8000/api/departamentos/');
        this.departamentos = response.data;
      } catch (error) {
        console.error('Error obteniendo departamentos:', error);
      }
    }
  }
};
</script>

<style scoped>
/* agregar ---- */
</style>
