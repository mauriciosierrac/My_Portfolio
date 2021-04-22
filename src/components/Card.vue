<template>
  <div class="card">
    <h4>{{ name }}</h4>
    <p>
      {{ description }}
    </p>
    
    <p><strong>Author: {{author}} </strong></p>
   
    <button-url :url="url"/>
    <button-url color="orange" :url="homepage" v-if="homepage != null" title="Deploy" />
   

  </div>
</template>

<script>
import ButtonUrl from './ButtonUrl.vue';
export default {
  components: { ButtonUrl },
  props: {
    name: String,
    description: String,
    author: String,
    url: String,
    homepage: String,
  },
};
</script>

<style scoped>
.card {
  border-radius: 5px;
  width: 250px;
  margin: 7px;
  text-align: center;
  border: solid 1px #eee;
  box-shadow: 1px 1px 4px #333;
  background:rgb(233, 230, 230);
}
</style>
