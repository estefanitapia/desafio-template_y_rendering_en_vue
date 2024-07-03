<template>
  <main class="container">
    <form class="form">
      <div>
        <label>Escribe un color de fondo en inglés</label>
        <br />
        <input class="form-control ancho" v-model="colorCuadrado" />
      </div>
      <div>
        <label>Escribe un color de letra en inglés</label>
        <br />
        <input class="form-control ancho" v-model="colorLetra" />
      </div>
      <div>
        <label>Mostrar texto</label>
        <input v-model="show" type="checkbox" />
      </div>
      <div>
        <label for="customRange2" class="form-label ancho">Borde</label>
        <br />
        <input
          v-model="border"
          type="range"
          class="form-range ancho"
          :min="minimo"
          :max="maximo"
          step="0.5"
          id="customRange2"
        />
      </div>
      <div>
        <label>Contenido textual: </label>
        <br />
        <textarea maxlength="200" v-model="texto"></textarea>
      </div>
      <div>
        <label>Tipografía: </label>
        <br />
        <select v-model="typography">
          <option
            :key="tipografia"
            v-for="tipografia in tipografias"
            :value="tipografia"
          >
            {{ tipografia }}
          </option>
        </select>
      </div>

      <div>
        <label>Opaco</label>
        <input v-model="opaco" type="checkbox" />
      </div>
      <div>
        <span>Tamaño de letra</span>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="p"
            value="1rem"
            v-model="size"
          />
          <label class="form-check-label fw-normal" for="p"> Pequeño </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="m"
            value="1.5rem"
            v-model="size"
          />
          <label class="form-check-label fw-normal" for="m"> Mediano </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="g"
            value="2rem"
            v-model="size"
          />
          <label class="form-check-label fw-normal" for="g"> Grande </label>
        </div>
      </div>
    </form>
    <figure
      id="cuadrado"
      :style="{
        background: colorCuadrado,
        color: colorLetra,
        borderRadius: radioCompleto,
        fontFamily: typography,
        fontSize: size,
      }"
      :class="{ opaco: opaco }"
    >
      <p v-if="show">{{ texto }}</p>
    </figure>
  </main>
</template>

<script>
export default {
  name: "ModidicarCuadro",
  data() {
    return {
      colorCuadrado: "",
      colorLetra: "",
      show: "",
      border: "",
      minimo: "1",
      maximo: "50",
      texto: "",
      typography: "",
      opaco: false,
      size: "",
      tipografias: [
        "Times New Roman",
        "Georgia",
        "Arial",
        "Verdana",
        "Tahoma",
        "Sanvito",
        "Courier",
      ],
    };
  },
  computed: {
    radioCompleto() {
      return this.border + "%";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.container {
  display: flex;
  align-items: stretch;
  gap: 2rem;
}

form {
  background: darkslategray;
  color: white;
  display: inline-block;
  flex-direction: flex-start;
  text-align: left;
  gap: 15px;
  padding: 40px;
  font-size: 16px;

  & > div {
    margin-top: 1rem;
  }
}

.ancho,
textarea,
select {
  width: 250px;
}

#cuadrado {
  width: 500px;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #ccc;
  margin-left: 50px;
  overflow: auto;
  padding: 1rem;
  align-self: center;
}

.opaco {
  opacity: 0.5; /* o cualquier valor de opacidad que desees */
}
</style>
