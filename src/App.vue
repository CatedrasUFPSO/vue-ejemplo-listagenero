<template>
  <div id="app">
    <ul>
      <li>Lista hombres</li>
      <li v-for="(hombre, index) in hombres" :key="index">
        {{ hombre.nombre }} - {{ hombre.edad }}
      </li>
    </ul>
    <br /><br />
    <ul>
      <li>Lista mujeres</li>
      <li v-for="(mujer, index) in mujeres" :key="index">
        {{ mujer.nombre }} - {{ mujer.edad }}
      </li>
    </ul>

    <label for="">Nombre </label>
    <input type="text" v-model="nuevoNombre" /><br />
    <label for="">Género </label>
    <input type="text" v-model="nuevoGenero" /><br />
    <label for="">edad </label>
    <input type="text" v-model="nuevaEdad" /><br />
    <button @click="addPersona">Añadir persona</button>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},

  data: function () {
    return {
      nuevoNombre: "",
      nuevoGenero: "",
      nuevaEdad: "",
      hombres: [],
      mujeres: [],
    };
  },

  methods: {
    addPersona() {
      const nuevaPersona = {
        nombre: this.nuevoNombre,
        edad: this.nuevaEdad,
        genero: this.nuevoGenero,
      };
      if (parseInt(this.nuevaEdad) >= 18) {
        if (this.nuevoGenero == "m") {
          this.hombres.push(nuevaPersona);
        } else {
          this.mujeres.push(nuevaPersona);
        }
      }

      this.nuevoNombre = "";
      this.nuevaEdad = "";
      this.nuevoGenero = "";
    },
  },
};
</script>

<style>
ul {
  width: 420px;
  margin: 0 auto;
  background: gainsboro;
  border-radius: 8px;
}
</style>
