<template>
  <h1>Neovis.js Simple Example</h1>
  <div id="viz">
    <button v-on:click="drawGraph">Draw</button>
  </div>
</template>

<script>
import NeoVis from "neovis.js";

export default {
  data() {
    return {
      viz: NeoVis,
      config: {}
    }
  },
  methods: {
    drawGraph: function () {
      this.config = {
        containerId: "viz",
        neo4j: {
          serverUrl: this.serverUrl,
          serverUser: this.serverUser,
          serverPassword: this.serverPassword,
        },
        labels: {
          "Character": {
            label: "name",
            value: "pagerank",
            group: "community"
          }
        },
        relationships: {
          INTERACTS: {
            value: "weight",
            caption: true,
            thickness: "weight",
          }
        },
        initialCypher: this.cypher, //"call db.schema.visualization()"
      };
      this.viz = new NeoVis.default(this.config);
      this.viz.render();
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
  width: 900px;
  height: 700px;
  border: 1px solid lightgray;
  font: 22pt arial;
}
</style>
