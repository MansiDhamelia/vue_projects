<template>
  <Header title="Todo list" />
  <Additem @add-task="addTask" />
</template>

<script>
import Additem from "./components/Additem.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Header,
    Additem,
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

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  cursor: pointer;
  font-size: 15px;
  font-family: inherit;
}
</style>
