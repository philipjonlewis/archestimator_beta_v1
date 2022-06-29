<script lang="ts">
  import "./styles/app.css";

  import PublicLayout from "./layouts/__PublicLayout.svelte";
  import { Route } from "svelte-navigator";
  import Home from "./routes/Home.svelte";
  import Tile from "./routes/estimates/Tile.svelte";
  import Paint from "./routes/estimates/Paint.svelte";
</script>

<PublicLayout>
  <Route path="/">
    <Home />
  </Route>
  <Route path="estimates/*" primary={false}>
    <Route path="/tile" primary={false}>
      <Tile />
    </Route>
    <Route path="/paint" primary={false}>
      <Paint />
    </Route>
  </Route>
</PublicLayout>

<style lang="scss">
</style>
