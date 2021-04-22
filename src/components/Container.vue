<template>
  <div id="container" class="container">
    <img
      src="https://avatars.githubusercontent.com/u/70919024?v=4"
      alt="Avatar de Mauricio"
      width="100"
      loading="lazy"
      class="image"
    />
    <h2>Welcome!</h2>
    <hr />
    <loading v-if="load" />
    <div class="cards" v-for="project in projects" :key="project.id">
      <Card
        :name="project.name"
        :description="project.description"
        :author="project.owner.login"
        :url="project.html_url"
        :homepage="project.homepage"
      />
    </div>
  </div>
</template>

<script>
import Card from "./Card";
import Loading from "./Loading.vue";

export default {
  data() {
    return {
      projects: null,
      load: false,
    };
  },
  components: {
    Card,
    Loading,
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    async getProjects() {
      this.load = true;
      const res = await fetch(
        "https://api.github.com/users/mauriciosierrac/repos"
      );
      const data = await res.json();
      this.load = false;
      this.projects = data;
      console.log(data);
    },
  },
};
</script>

<style scoped>
.image {
  border-radius: 50%;
  margin: 15px
}

.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.container {
  overflow: hidden;
  text-align: center;
  border: solid 1px #eee;
  box-shadow: 1px 1px 4px #333;
  background: snow;
  border-radius: 10px;
  margin: auto;
  margin-top: 15px;
  margin-bottom: 15px;
}
</style>
