<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <GraphArea
      server-url="bolt://44.198.170.209:7687"
      server-user="neo4j"
      server-password="launcher-sleds-darts"
      cypher="call db.schema.visualization()"/>
</template>

<script>
import GraphArea from "@/components/GraphArea";

export default {
  name: 'App',
  components: {
    GraphArea
  }
}
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
