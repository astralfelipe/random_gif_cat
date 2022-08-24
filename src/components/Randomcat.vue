<template>
  <div>
    <h1>{{ msg }}</h1>
    <form @submit.prevent="getCat">
      <div class="form__input-container">
        <div class="row form-group">
          <div class="col-6 d-flex flex-column align-items-end">
            <label for="text">Titulo</label>
            <label for="text">Filtro</label>
            <label for="text">Color</label>
            <label for="text">Tamaño</label>
          </div>
          <div class="col-6 d-flex flex-column align-items-start">
            <input type="text" v-model="title" />
            <select v-model="filter" name="" id="">
              <option disabled value="">Selecciona Filtro</option>
              <option value="blur">Blur</option>
              <option value="mono">Mono</option>
              <option value="sepia">Sepia</option>
              <option value="negative">Negative</option>
              <option value="paint">Paint</option>
              <option value="pixel">Pixel</option>
            </select>
            <div class="d-flex">
              <select v-model="color" name="" id="">
                <option disabled value="">Selecciona Color</option>
                <option value="red">Rojo</option>
                <option value="blue">Azul</option>
                <option value="green">Verde</option>
                <option value="white">Blanco</option>
                <option value="yellow">Amarillo</option>
              </select>
              <div class="circle" :style="{'background-color': color}"></div>
            </div>
            <input v-model.number="size" type="number" name="" id="" />
          </div>
        </div>
      </div>

      <input class="mt-3" type="submit" value="Obtener mi gatito" />
    </form>
    <div class="spinner-border" :class="{ 'd-none': !loading }" role="status">
      <span class="sr-only">Loading...</span>
    </div>
    <img :src="image" />
  </div>
</template>

<script>
export default {
  name: "Random Gif Cat",
  props: {
    msg: String,
  },
  data() {
    return {
      title: "",
      filter: "",
      color: "",
      size: 100,
      image: "",
      loading: false,
    };
  },
  methods: {
    getCat() {
      this.loading = true;
      fetch(
        `https://cataas.com/cat/gif/says/${this.title}?filter=${this.filter}&color=${this.color}&size=${this.size}`
      ).then((data) => {
        this.image = data.url;
        this.loading = false;
      });
    },
  },
};
</script>

<style scoped>
h1 {
  font-size: 2em;
  font-weight: 700;
  text-align: center;
  padding: 2em 0 1em;
}
.form__input-container {
  background-color: lightcoral;
  padding: 1em;
}
.form__input-group {
  margin: 1em;
  text-align: left;
}
.circle {
  height: 50px;
  width: 50px;
  border-radius: 50%;
  background-color: white;
  display: inline-block;
  margin-left: 1em;
}
</style>
