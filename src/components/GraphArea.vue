<template>
  <form>
    <fieldset>
      <legend>Query Neo4j</legend>

      <label for="boltField">Bolt Host URL</label>
      <input type="text"
             placeholder="d7ade437.databases.neo4j.io"
             id="boltField">
      <br>
      <label for="usernameField">Username</label>
      <input type="text"
             placeholder="neo4j"
             id="usernameField">
      <br>
      <label for="passwordField">Password</label>
      <input type="password"
             placeholder=""
             id="passwordField">
      <br>
      <label for="cypherField">Cypher</label>
      <textarea rows="10" cols="80"
                placeholder="MATCH (n) RETURN n LIMIT 10"
                id="cypherField"/>
      <br>
      <button class="draw-button" type="button" v-on:click="drawGraph">Query</button>
    </fieldset>
  </form>
  <div id="viz"/>
</template>

<script>
import NeoVis from "neovis.js";

export default {
  methods: {
    drawGraph: function () {
      let viz;
      let config = {
        containerId: "viz",
        neo4j: {
          serverUrl: this.serverUrl,
          serverUser: this.serverUser,
          serverPassword: this.serverPassword
        },
        initialCypher: this.cypher
      };

      viz = new NeoVis(config);
      viz.render();
    }
  },
  name: "GraphArea",
  props: {
    serverUrl: String,
    serverUser: String,
    serverPassword: String,
    cypher: String,
  }
}
</script>

<style scoped>
#viz {
  margin-top: 3em;
  width: 20em;
  height: 20em;
  border: 1px solid lightgray;
  font: 22pt arial;
}

.draw-button {
  background-color: #13aa52;
  border: 1px solid #13aa52;
  border-radius: 4px;
  box-shadow: rgba(0, 0, 0, .1) 0 2px 4px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  font-family: "Akzidenz Grotesk BQ Medium", -apple-system, BlinkMacSystemFont, sans-serif;
  font-size: 16px;
  font-weight: 400;
  outline: none;
  outline: 0;
  padding: 10px 25px;
  text-align: center;
  transform: translateY(0);
  transition: transform 150ms, box-shadow 150ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  margin: 25px;
}

.draw-button:hover {
  box-shadow: rgba(0, 0, 0, .15) 0 3px 9px 0;
  transform: translateY(-2px);
}

@media (min-width: 768px) {
  .draw-button {
    padding: 10px 30px;
  }
}
</style>
