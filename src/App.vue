<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <p>{{ name }}</p>

  <Form msg="Welcome to Your Vue.js App" @nameChange="updateName($event)" />
</template>

<script>
import Form from './components/Form.vue';

export default {
  name: 'App',
  components: {
    Form,
  },
  data() {
    return {
      name: '',
    };
  },
  methods: {
    updateName(name) {
      this.name = name;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
