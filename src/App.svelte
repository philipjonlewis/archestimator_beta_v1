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

  import { Icon, Cog } from "svelte-hero-icons";
</script>

<main>
  <PublicLayout>
    <!-- <Route path="/" primary={false} component={Home} />
    <Route path="about" primary={true} component={About} />
    <Route path="contact" primary={false} component={Contact} /> -->
    <Route path="/*" primary={false}>
      <Tile />
      <!-- <ContentLayout> -->
      <!-- <Route path="/" primary={false} component={Estimates} /> -->
      <!-- <Route path="/" primary={false} component={Tile} /> -->
      <!-- <p>helo</p> -->
      <!-- <Route path="/paint" primary={false} component={Paint} />
        <Route path="/chb" primary={false} component={ConcreteBlocks} />
        <Route path="/wood" primary={false} component={Wood} />
        <Route path="/hardware" primary={false} component={Hardware} /> -->
      <!-- </ContentLayout> -->
    </Route>
  </PublicLayout>
</main>

<style global lang="scss">
  .home-content {
    @apply mt-2;
    height: 100%;
    /* background-color: blue; */
  }

  // main {
  //   @apply bg-neutral-100;
  //   height: 100vh;
  //   widows: 100vw;
  //   overflow: hidden;
  //   display: flex;
  //   flex-direction: column;
  //   justify-content: center;
  //   align-items: center;

  //   .message-container {
  //     @apply bg-orange-100 px-4 py-16 rounded-lg;
  //     display: flex;
  //     flex-direction: column;
  //     justify-content: center;
  //     align-items: center;
  //     // background-color: orange;
  //     svg {
  //       @apply bg-white w-fit rounded-full;
  //       height: 3rem;
  //       color: rgb(255, 128, 0);
  //     }

  //     p {
  //       @apply text-neutral-600;
  //     }

  //     p:first-of-type {
  //       @apply text-sm pt-2;
  //     }

  //     p {
  //       @apply text-base;
  //     }
  //   }
  // }
</style>
