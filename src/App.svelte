<script lang="ts">
  import { fade, fly } from "svelte/transition";
  // import Styles from "./styles/styles.svelte";
  import PublicLayout from "./layouts/__PublicLayout.svelte";
  import { Route } from "svelte-navigator";

  import Home from "./routes/Home.svelte";
  import About from "./routes/About.svelte";
  import Contact from "./routes/Contact.svelte";
  import {
    Tile,
    Paint,
    ConcreteBlocks,
    Wood,
    Hardware,
    Estimates,
  } from "./routes/estimates";

  import ContentLayout from "./layouts/__ContentLayout.svelte";
</script>

<main>
  <!-- <Styles /> -->
  <PublicLayout>
    <Route path="/" primary={false} component={Home} />
    <Route path="about" primary={false} component={About} />
    <Route path="contact" primary={false} component={Contact} />

    <Route path="estimates/*" primary={false}>
      <ContentLayout>
        <Route path="/" primary={false} component={Estimates} />
        <Route path="/tile" primary={false} component={Tile} />
        <Route path="/paint" primary={false} component={Paint} />
        <Route path="/chb" primary={false} component={ConcreteBlocks} />
        <Route path="/wood" primary={false} component={Wood} />
        <Route path="/hardware" primary={false} component={Hardware} />
      </ContentLayout>
    </Route>
  </PublicLayout>
</main>

<style global>
  .home-content {
    @apply mt-2;
    height: 100%;
    /* background-color: blue; */
  }
</style>
