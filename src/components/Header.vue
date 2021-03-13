<template>
  <div>
    <nav>
      <h1>VIDEO TV</h1>
      <a @click="isClicked()" href="#">Agregar video</a>
    </nav>
    <form v-if="clicked" v-on:submit.prevent="getInfoForm">
      <input type="text" name="tittle" />
      <input type="text" name="description" />
      <button>Agregar</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clicked: null,
      tittle: null,
      description: null,
    };
  },
  methods: {
    getInfoForm(e) {
      this.tittle = e.target.elements.tittle.value;
      this.description = e.target.elements.description.value;
      this.clicked = false;
    },
    isClicked() {
      this.clicked = true;
    },
  },
};
</script>

<style scoped>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: rgb(226, 82, 63);
  padding: 1.3rem;
  border-radius: 20px;
}
h1 {
  font-size: 1.9rem;
  color: white;
}
nav a {
  text-decoration: none;
  color: white;
  font-size: 1.2rem;
}
</style>