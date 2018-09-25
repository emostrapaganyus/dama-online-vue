<template>
  <div id="app" class="row">
    <Menu></Menu>
    <GameArea></GameArea>
    <ScoreBoard></ScoreBoard>
  </div>
</template>

<script>
import Menu from "./components/Menu";
import ScoreBoard from "./components/ScoreBoard";
import GameArea from "./components/GameArea";
import { Col } from 'bootstrap-vue';

export default {
  name: "app",
  components: { ScoreBoard, GameArea, Menu },
  data() {
    return {};
  }
};
</script>

<style>
body {
  margin: 0;
  width: 100%;
  height: 100%;
}

#app {
  font-family: monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: 100%;
  height: 100%;
}
h1,
h2,
h3 {
  margin: 0;
}

.row{
  margin: 0 !important;
}
</style>
