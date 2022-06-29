<script>
  import { Router, Link } from "svelte-navigator";
</script>

<nav
  class="flex justify-between items-center mb-2 py-6 font-sans text-sm border-b-[1px] border-gray-300 "
>
  <div>
    <Link to="/"><p class="logo">archestimator.</p></Link>
  </div>
  <div class="flex gap-4">
    <Link to="/estimates/tile">Tile Estimates</Link>
    <Link to="/estimates/paint">Paint Estimates</Link>
  </div>
</nav>

<style lang="scss">
  .logo {
    @apply text-orange-600 text-xl font-semibold;
    // background-color: yellow;

    font-family: "Space Grotesk", sans-serif;
  }
</style>
