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
  <div class="content">
    <nav
      class="bg-neutral-800 text-white flex flex-row justify-between items-center px-4 py-4 relative rounded-lg"
    >
      <div class="flex flex-row items-center">
        <div class="mr-4 text-lg font-bold pr-4 border-r-[1px]">
          <p>archestimator.</p>
        </div>
        <ul class="flex gap-8 text-xs font-semibold">
          <li class="border-b-[1px]">Home</li>
          <li>About</li>
          <li>Contact</li>
        </ul>
      </div>
      <div>
        <ul class="flex gap-6 text-sm">
          <li
            class="bg-neutral-700 py-2 px-8 rounded-md text-sm font-semibold hover:bg-red-500 cursor-pointer hover:-translate-y-0.5 transition hover:shadow-md"
          >
            Sign Up
          </li>
          <li
            class="bg-neutral-700 py-2 px-8 rounded-md text-sm font-semibold hover:bg-yellow-500 cursor-pointer hover:-translate-y-0.5 transition hover:shadow-md"
          >
            Log In
          </li>
        </ul>
      </div>
    </nav>

    <div class="hero-container">
      <div class="text-left md:text-center flex flex-col p-4">
        <p class=" text-5xl md:text-6xl font-semibold mb-4">
          Architectural cost estimation made easy
        </p>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit eos
          sequi officia quia molestiae ducimus alias est quas culpa eius.
        </p>
      </div>
    </div>
  </div>

  <!-- <div class="curve">hi</div> -->
</main>

<style global lang="scss">
  main {
    @apply bg-neutral-900 min-w-full min-h-screen;

    .content {
      @apply container mx-auto pt-4 flex flex-col gap-4;
    }

    .hero-container {
      @apply rounded-lg bg-neutral-800 text-white  flex flex-col justify-center items-center h-64;

      .text {
        // @apply mr-4 mb-8;
        // text-align: center;
        // max-width: 56rem;
        // @apply ;
      }

      .cta {
        @apply text-white bg-yellow-500   rounded-lg shadow-lg p-4 w-96 h-96;

        .title-container {
          @apply text-xl font-semibold border-b-[1px] pb-4 mb-4;
        }
      }
    }
  }
</style>
