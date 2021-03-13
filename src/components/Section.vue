<template>
  <div class="course-list">
    <h2>Lista de Videos</h2>
    <div class="course-list-info">
      <div
        v-for="(course, index) in courses"
        :key="course.id"
        class="card-info"
      >
        <button @click="removeElement(index)" class="btnRemove">x</button>
        <div class="card-image">
          <img :src="[course.src]" alt="" />
        </div>
        <p class="card-tittle">{{ course.tittle }}</p>
        <p class="card-description">{{ course.description }}</p>
        <div class="card-button">
          <button>Ver detalle</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      courses: null,
    };
  },
  methods: {
    getInfo() {
      axios.get("http://localhost:3000/courses").then((response) => {
        this.courses = response.data;
      });
    },
    removeElement(index) {
      this.courses.splice(index, 1);
    },
  },
  created() {
    this.getInfo();
  },
};
</script>

<style scoped>
.card-info {
  position: relative;
  width: 350px;
  height: 450px;
  border: 1px solid grey;
}
.card-image img {
  width: 350px;
}
.card-tittle {
  text-align: center;
}
.card-button {
  display: flex;
  justify-content: center;
}
.card-button button {
  background-color: rgb(38, 207, 207);
  width: 90%;
  padding: 0.8rem;
  border: none;
  color: white;
  border-radius: 10px;
  cursor: pointer;
}
.course-list-info {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
.btnRemove {
  position: absolute;
  padding: 3px 15px;
  background-color: transparent;
  border: none;
  cursor: pointer;
}
</style>