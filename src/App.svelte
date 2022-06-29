<script lang="ts">
  import { fade, fly } from "svelte/transition";
  import Styles from "./styles/styles.svelte";
  import PublicLayout from "./layouts/__PublicLayout.svelte";
  import { Route } from "svelte-navigator";
  import Home from "./routes/Home.svelte";
  import Tile from "./routes/estimates/Tile.svelte";
  import Paint from "./routes/estimates/Paint.svelte";
  import ConcreteBlocks from "./routes/estimates/ConcreteBlocks.svelte";
  import Wood from "./routes/estimates/Wood.svelte";
  import Hardware from "./routes/estimates/Hardware.svelte";
</script>

<PublicLayout>
  <Route path="/" primary={false}>
    <Home />
  </Route>

  <Route path="estimates/*" primary={false}>
    <Route path="/tile" primary={false}>
      <Tile />
    </Route>
    <Route path="/paint" primary={false}>
      <Paint />
    </Route>
    <Route path="/chb" primary={false}>
      <ConcreteBlocks />
    </Route>
    <Route path="/wood" primary={false}>
      <Wood />
    </Route>
    <Route path="/hardware" primary={false}>
      <Hardware />
    </Route>
  </Route>
</PublicLayout>
