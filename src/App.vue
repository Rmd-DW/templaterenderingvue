<template>
  <div id="App" class="app">
    <div class="interfaz">
      <form>
        <label>Color de fondo</label>
        <input type="color" v-model="fondo" />

        <label>Color de texto</label>
        <select v-model="colortext">
          <option v-for="color in colores" :key="color" :value="color">{{ color }}</option>
        </select>

        <ul>
          <li>
            <label>Mostrar texto</label>
            <input v-model="shownombre" name="shownombre" type="checkbox" />
          </li>
        </ul>

        <label>Contenido textual</label>
        <textarea v-model="contenidoTextual"></textarea>

        <label>Tipografía</label>
        <select v-model="tipography">
          <option v-for="tipografia in tipographies" :key="tipografia" :value="tipografia">{{ tipografia }}</option>
        </select>

        <ul>
          <li>
            <label>Opaco</label>
            <input v-model="showopacity" name="showopacity" type="checkbox" />
          </li>
        </ul>

        <label>Tamaño de letra</label>
        <ul class="list-radio">
          <li>
            <label>pequeño</label>
            <input v-model="letersize" type="radio" value="12px" />
          </li>
          <li>
            <label>mediano</label>
            <input v-model="letersize" type="radio" value="16px" />
          </li>
          <li>
            <label>grande</label>
            <input v-model="letersize" type="radio" value="20px" />
          </li>
        </ul>

        <label>Borde radio</label>
        <input type="range" v-model="borderRadius" min="0" max="150" />
      </form>
    </div>

    <div :style="{ background: fondo, borderRadius: borderRadius + 'px' }" class="resultado">
      <div :class="{ opacidad: showopacity }">
        <span :style="{ color: colortext, fontStyle: tipography, fontSize: letersize }" v-show="shownombre">{{ contenidoTextual }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      fondo: "#1dbe66", // Valor por defecto para el color de fondo
      colortext: "",
      colores: ["green", "purple", "darkgreen", "red", "yellow", "black", "white"],
      shownombre: true,
      contenidoTextual: "",
      tipographies: ["normal", "italic"],
      tipography: "normal",
      showopacity: true,
      letersize: "16px", 
      borderRadius: 30 
    };
  }
};
</script>

<style scoped>
.app {
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: lighter;
}

label {
  color: white;
}

form {
  display: flex;
  flex-direction: column;
}

ul {
  list-style: none;
  text-decoration: none;
  padding: 0;
}

.interfaz {
  flex-direction: column;
  margin: 1rem;
  padding: 3rem;
  background-color: #2f4f4f;
}

.resultado {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 1rem;
  padding: 1rem;
  background-color: #1dbe66;
  width: 300px;
  height: 300px;
  border-radius: 30%;
}

.opacidad {
  opacity: 0.5;
}

.list-radio {
  display: flex;
  gap: 1rem; 
}
</style>
