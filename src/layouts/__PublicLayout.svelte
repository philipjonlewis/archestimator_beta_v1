<script>
  import { Router, Link } from "svelte-navigator";
</script>

<Router>
  <div class="container h-screen mx-auto flex flex-col justify-between">
    <nav
      class="flex justify-between items-center mb-2 py-6 font-sans text-sm border-b-[1px] border-gray-300 "
    >
      <div class="logo">
        <Link to="/">archestimator.</Link>
      </div>
      <div class="flex gap-4">
        <Link to="/estimates/tile">Tile Estimates</Link>
        <Link to="/estimates/paint">Paint Estimates</Link>
      </div>
    </nav>

    <div class="container h-full ">
      <slot />
    </div>

    <footer class=" py-6 mt-2 border-t-[1px] border-gray-300 ">Footer</footer>
  </div>
</Router>

<style lang="scss">
  .logo {
    color: red;
  }
</style>
